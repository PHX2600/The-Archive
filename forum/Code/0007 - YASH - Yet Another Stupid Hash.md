## YASH - Yet Another Stupid Hash
Posted by **opcode** on Fri December 28th, 2007 12:51:45 AM

Minddog and I (opcode) worked on this one. Basics:  The input buffer, buffer_in,
must always be 16 bytes in size.  All data should be padded to this size. The
output buffer, buffer_out is the result of the operations below.  It is also
16-bytes in size. This is the code to calculate the hash:

	; *************************************************
	;  This code is licensed under the GPl v2.
	;
	;  SYSTEM REQUIREMENTS:
	;   AMD/Intel x86 CPU with SSE2 support.
	; -------------------------------------------------
	; INPUT:
	;  A 16-byte global variable called 'buffer_in'.
	;
	; OUTPUT:
	;   A 16-byte hashed value in a 16-byte global
	;   variable called 'buffer_out'.
	;
	; RETURNS:
	;  -1 if SSE2 is not supported.
	;  General protection fault if I/O buffers are misaligned.
	; -------------------------------------------------
	;  This code works best when 'yash_main' is aligned to
	;  a 64-byte cache line size.

	; *************************************************
	;  yash_init should be jumped to *ONLY ONCE* to
	;  intialize the SSE2 unit on the CPU.
	yash_init:
		mov	eax, 0x00000001
		cpuid
		xor	eax, eax
		not	eax
		bt	edx, 26		; Test for SSE2
		jc	yash_start
		ret
	yash_start:
		movaps	xmm0, xmm0	; Initialize MMX/SSE/SSE2/3/4 unit
	; *************************************************
	;  If looping more than once, have the routine
	;  loop back to 'yash_main' and *NOT* yash_init.
	yash_main:
		; edx = A3, ecx = A2, ebx = A1, eax = A0
		lea	eax, buffer_in
		mov	ebx, [eax + 0x04]
		mov	ecx, [eax + 0x08]
		push	ebx
		mov	edx, [eax + 0x0C]
		not	ebx
		mov	eax, [eax]

	   	; Step 2: H3 = H3 + (A3 ^ (A2 + (~A1 ^ A0)))
		xor	ebx, eax
		add	ebx, ecx
		xor	edx, ebx
		add	[buffer_out + 0x0C], edx
		pop	ebx
		lea	edx, buffer_out

		; Step 1: H0 = H0 + A0
		add	[edx], eax

		; Step 4: H1 = H1 + (A2 + A1)
		mov	eax, ebx
		add	ebx, ecx
		add	[edx + 0x04], ebx

		; Step 3: H2 = H2 + (~A2 ^ A1)
		not	ecx
		mov	ebx, eax
		xor	ebx, ecx
		add	[edx + 0x08], ebx

		; Rotate left one bit
	yash_rotate:
		mov	eax, [edx + 0x04]
		mov	ecx, [edx + 0x0C]

		; x86 and SSE2 instructions are interleaved for parallelism.
		rcl	eax, 1
		movaps	xmm0, [edx]
		and	eax, 0x00000001
		psllq	xmm0, 1
		rcl	ecx, 1
		and	ecx, 0x00000001
		movaps	[edx], xmm0

		add	[edx + 0x08], eax
		add	[edx], ecx
	; End of code
