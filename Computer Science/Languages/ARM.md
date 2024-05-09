ARM is an [[Assembly|instruction set]] made by the 



# ARM Variants
There are a variety of common ARM variants. The main variant are **ARMv1** through **ARMv9**. These are the series of ARM instruction sets that have been developed currently. **ARMv8** and ARMv9 have the special ability to use both 32 and 64-bit instructions. This is commonly called ARM64/AArch64 or ARM32/AArch32. Finally Thumb32 (T32) is a variable length instruction set supporting 32-bit and 16-bit instructions.


# Registers
The [[Memory#Registers|registers]] found within ARM can be classified into three main categories GPR, FPR, and SPR. 

## General Purpose Registers
General purpose registers (GPR) are registers which are commonly used for basic operations. There are 31 GPRs ranging from `r0` to `r30` all having a 64-bit length. The `r29` register is used as the **frame pointer**, and `r30` is used as the **link register**. There also exists a **zero register** which is a read-only register containing 0 used for no immediate  value argument is available. This register can be called as `wzr`/`xzr` depending on the form.

GPRs can either be used as **extended** or **non-extended**. Extended is when an instruction uses all 64-bits of the GPR. This extended form is expressed as `xD`, where `D` is the register's number. In non-extended form only the lower 32-bits are used. This is expressed as `wD`. 

## Floating point registers
Floating point registers (FPR) are registers which are used for [[Floating Point Numbers|floating point operations]].

## Special purpose registers
Special purpose registers (SPR)

# Instructions


The format of instructions come in four types. These formats specify a destination register as there first argument `rD`, then addition argument operations `rA`/`rB`, and the possibly an immediate value `VALUE`. The four formats are:
- `rD, rA, rB`
- `rD, rA`
- `rD, rA, VALUE`
- `rD, VALUE`

## Maths Operations
All basic maths operations (`add` and `sub`) have two variants, one for extended and another for non-extended registers. In addition to this they also have an operation that can take **Arithmetic Immediate Values**. These values are of the type `UIMM12`, `UIMM24`, and `NIMM25`. In general conversion into this type is automatic. In general an AIMM value should be prepended by a `#`, however some assemblers don't require this.

Operations such as division and multiplication also have a signed and unsigned format but lack immediate operations. Divison has the instructions `udiv` and `sdiv` respectively. While multiplication has `mul` for signed and `smull` and `umull` for specifically non-extended register values into an extended register.

Negation can be done with `neg`.

`Mov` operations can

# Data Types
There are a few different common datatypes used within: There are:
- `SIMM12`/`SIMM32`/`Siim64` signed values.
- `UIMM12`/`UIMM32`/`Uiim64` unsigned values.