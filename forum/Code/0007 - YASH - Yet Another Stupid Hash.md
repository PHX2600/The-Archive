## YASH - Yet Another Stupid Hash
Posted by **opcode** on Fri December 28th, 2007 12:51:45 AM

Minddog and I (opcode) worked on this one.
Basics:  The input buffer, buffer_in, must always be 16 bytes in size.  All data should be padded to this size.
The output buffer, buffer_out is the result of the operations below.  It is also 16-bytes in size.
This is the code to calculate the hash:
[code:1po81pdn]
; *************************************************
;  This code is licensed under the GPl v2&#46;
;
;  SYSTEM REQUIREMENTS&#58;
;   AMD/Intel x86 CPU with SSE2 support&#46;
; -------------------------------------------------
; INPUT&#58;
;  A 16-byte global variable called 'buffer_in'&#46;
;
; OUTPUT&#58;
;   A 16-byte hashed value in a 16-byte global
;   variable called 'buffer_out'&#46;
;
; RETURNS&#58;
;  -1 if SSE2 is not supported&#46;
;  General protection fault if I/O buffers are misaligned&#46;
; -------------------------------------------------
;  This code works best when 'yash_main' is aligned to
;  a 64-byte cache line size&#46;

; *************************************************
;  yash_init should be jumped to *ONLY ONCE* to
;  intialize the SSE2 unit on the CPU&#46;
yash_init&#58;
	mov	eax, 0x00000001
	cpuid
	xor	eax, eax
	not	eax
	bt	edx, 26		; Test for SSE2
	jc	yash_start
	ret
yash_start&#58;
	movaps	xmm0, xmm0	; Initialize MMX/SSE/SSE2/3/4 unit
; *************************************************
;  If looping more than once, have the routine
;  loop back to 'yash_main' and *NOT* yash_init&#46;
yash_main&#58;
	; edx = A3, ecx = A2, ebx = A1, eax = A0
	lea	eax, buffer_in
	mov	ebx, &#91;eax + 0x04&#93;
	mov	ecx, &#91;eax + 0x08&#93;
	push	ebx
	mov	edx, &#91;eax + 0x0C&#93;
	not	ebx
	mov	eax, &#91;eax&#93;

   	; Step 2&#58; H3 = H3 + (A3 ^ (A2 + (~A1 ^ A0)))
	xor	ebx, eax
	add	ebx, ecx
	xor	edx, ebx
	add	&#91;buffer_out + 0x0C&#93;, edx
	pop	ebx
	lea	edx, buffer_out

	; Step 1&#58; H0 = H0 + A0
	add	&#91;edx&#93;, eax

	; Step 4&#58; H1 = H1 + (A2 + A1)
	mov	eax, ebx
	add	ebx, ecx
	add	&#91;edx + 0x04&#93;, ebx

	; Step 3&#58; H2 = H2 + (~A2 ^ A1)
	not	ecx
	mov	ebx, eax
	xor	ebx, ecx
	add	&#91;edx + 0x08&#93;, ebx

	; Rotate left one bit
yash_rotate&#58;
	mov	eax, &#91;edx + 0x04&#93;
	mov	ecx, &#91;edx + 0x0C&#93;

	; x86 and SSE2 instructions are interleaved for parallelism&#46;
	rcl	eax, 1
	movaps	xmm0, &#91;edx&#93;
	and	eax, 0x00000001
	psllq	xmm0, 1
	rcl	ecx, 1
	and	ecx, 0x00000001
	movaps	&#91;edx&#93;, xmm0

	add	&#91;edx + 0x08&#93;, eax
	add	&#91;edx&#93;, ecx
; End of code
[/code:1po81pdn]
