	.section	__TEXT,__text,regular,pure_instructions
	.build_version macos, 11, 0	sdk_version 11, 1
	.intel_syntax noprefix
	.globl	_myFunction             ## -- Begin function myFunction
	.p2align	4, 0x90
#purpose of this function is to take two input parameters and output their sum.
_myFunction:                            ## @myFunction
	.cfi_startproc
## %bb.0:
	push	ebp  # establishing stack-frame
	.cfi_def_cfa_offset 8 #CFA register value plus offset of 8
	.cfi_offset ebp, -8  
	mov	ebp, esp 
	.cfi_def_cfa_register ebp
	push	eax 
	mov	eax, dword ptr [ebp + 12] # get first param from address space ebp+12 into eax =a 
	mov	ecx, dword ptr [ebp + 8] # get 2nd param from address space ebp+8 into ecx 
	mov	edx, dword ptr [ebp + 8] #also uses same address space ebp+8 into edx as local var, so it should contain value of 2nd input param
	add	edx, dword ptr [ebp + 12] # edx +=eax (adds value at address ebp+12, which is 1st input param, to local var, which is value of 2nd input param) 
	mov	dword ptr [ebp - 4], eax ## 4-byte Spill --> moves eax to avoid spillage		
	mov	eax, edx # eax = edx -->moves value of edx into eax (accumulator) as return value
	add	esp, 4 #  esp +=4 same as pop –4 bytes taken from stack pointer
	pop	ebp
	ret
	.cfi_endproc
                                        ## -- End function
	.globl	_main                   ## -- Begin function main
	.p2align	4, 0x90
_main:                                  ## @main
	.cfi_startproc
## %bb.0:
	push	ebp
	.cfi_def_cfa_offset 8
	.cfi_offset ebp, -8
	mov	ebp, esp
	.cfi_def_cfa_register ebp
	sub	esp, 24
	call	L1$pb
L1$pb:
	pop	eax
	mov	ecx, dword ptr [ebp + 12]
	mov	edx, dword ptr [ebp + 8]
	mov	dword ptr [ebp - 4], 0
	mov	dword ptr [ebp - 8], -1
	cmp	dword ptr [ebp + 8], 2
	mov	dword ptr [ebp - 12], eax ## 4-byte Spill
	jle	LBB1_2
## %bb.1:
	mov	eax, dword ptr [ebp + 12]
	mov	eax, dword ptr [eax + 4]
	mov	dword ptr [esp], eax
	call	_atoi
	mov	ecx, dword ptr [ebp + 12]
	mov	ecx, dword ptr [ecx + 8]
	mov	dword ptr [esp], ecx
	mov	dword ptr [ebp - 16], eax ## 4-byte Spill
	call	_atoi
	mov	ecx, dword ptr [ebp - 16] ## 4-byte Reload
	mov	dword ptr [esp], ecx
	mov	dword ptr [esp + 4], eax
	call	_myFunction
	mov	ecx, dword ptr [ebp - 12] ## 4-byte Reload
	lea	edx, [ecx + L_.str-L1$pb]
	mov	dword ptr [ebp - 8], eax
	mov	eax, dword ptr [ebp - 8]
	mov	dword ptr [esp], edx
	mov	dword ptr [esp + 4], eax
	call	_printf
LBB1_2:
	xor	eax, eax
	add	esp, 24
	pop	ebp
	ret
	.cfi_endproc
                                        ## -- End function
	.section	__TEXT,__cstring,cstring_literals
L_.str:                                 ## @.str
	.asciz	"%d\n"

.subsections_via_symbols


