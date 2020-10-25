# rockchip-dptx-re


## Quick start

### Software dependencies

* Python 3
* [Kaitai Struct Compiler][ksc]
* [Kaitai Struct Python Runtime][kspr]

### Procedure

1. Install dependencies.
2. Download the DPTX binaries by running `./download.sh`.
3. Run `make` to generate the parser code used by `extract_fw.py`.
4. Extract the code and data sections from each binary with
   `./extract_fw.py ...`, where `...` is the name of the DPTX firmware
   binary.


## Reverse engineering notes

See [Notes.md](./Notes.md).


[ksc]: https://github.com/kaitai-io/kaitai_struct_compiler
[kspr]: https://github.com/kaitai-io/kaitai_struct_python_runtime


Some additional notes and suggestions: 

If you want to reverse engineer that binary, probably the most efficient way to do that now would be to open the binary up in Ghidra with the Xtensa module (https://github.com/yath/ghidra-xtensa), since Ghidra can decompile the binary in addition to just disassembling it. That way, you wouldn't have to learn the whole ISA in order to understand roughly what the code is doing. It would be nice

if there was Xtensa support for Unicorn Engine, though, because then you could build a custom emulator for the chip and, if you hacked the dptx kernel driver so it doesn't really touch the core and only forwards read/writes to its internal memory, you could completely trace the execution of the binary and all its MMIO accesses.
