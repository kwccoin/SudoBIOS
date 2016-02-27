SudoBIOS - a completely transparent 32 bit protected mode BIOS extender - say goodbye to real mode code. SudoBIOS uses simple mode switching, address translation and buffering to provide interrupt based classic mode (Compatibility Support Module) BIOS services while in 32 bit protected mode.

The mbr loads SudoBIOS as a 2nd stage (to absolute address 0x2000). A far call to that location returns in 32 bit protected mode. A subset of the native BIOS functions (the common usable ones) are supported.

SudoBIOS is written in FASM (2700+ lines of Intel syntax x86 assembly language) and will assemble as is in FASM and NASM. Both output files are essentially the same (with NASM -O2). The only insignificant difference is the order of the operand (0x66) and address (0x67) override opcode pairing of the 2 assemblers. Note, the distibution binary is assembled in FASM and utilizes a FASM align macro to better populate the alignment fill. 

There is a SudoBIOS demo. It's a 16MB FAT12 partitioned hard drive USB flash drive image of the real mode MikeOS converted to 32 bit, running in 32 bit protected mode and accessing BIOS services transparently through SudoBIOS. It will boot and run on real hardware and QEMU and BOCHS.

The source code is also available as well as the fat(ter)12 source code which includes the mbr.asm and a simple 4K PM32 FAT12 boot loader.