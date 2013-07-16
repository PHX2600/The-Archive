## Coinciding Bitwise AND/OR Using Bitwise Operator Selection
Posted by **jargon** on Fri January 1st, 2010 02:10:49 PM

<!-- s;) --><img src="{SMILIES_PATH}/icon_e_wink.gif" alt=";)" title="Wink" /><!-- s;) --> *very useful!* I figured out this neato trick! <!-- s:D --><img src="{SMILIES_PATH}/icon_e_biggrin.gif" alt=":D" title="Very Happy" /><!-- s:D -->

[code:o5k34cqj]'Coinciding Bitwise AND/OR Using Bitwise Operator Selection
'by T&#46;R&#46;Keal of http&#58;//thekealshow&#46;com/
'Use any way you wish and feel free to make unlimited derivative works!

'Performs a 32bit coinciding bitwise AND/OR between arguments A,B
'Use BitMask argument with True bits for OR, False bits for AND
'Each bit may be toggled independently in BitMask

const BITMASK_AND=&amp;H00000000
const BITMASK_OR=&amp;HFFFFFFFF

function bitmask_operator (A as uinteger, B as uinteger, BitMask as uinteger) as uinteger   
    return ((A and B) and not(BitMask xor BITMASK_AND)) or ((A or B) and not(BitMask xor BITMASK_OR))
end function[/code:o5k34cqj]
