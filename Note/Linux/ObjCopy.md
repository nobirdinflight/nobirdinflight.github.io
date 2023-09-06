- [命令ObjCopy](#命令objcopy)
  - [作用](#作用)
  - [用法](#用法)

命令ObjCopy
===

作用
---
objcopy将一个二进制可执行文件(coff, elf)修改，转换到另一个新的二进制文件，类似对string操作后生成一个新的string。

具体的功能包括:

1. 删除符号表、调试信息
2. coff与elf的相互转换
3. 修改节区

用法
---
```
objcopy [-F bfdname|--target=bfdname] 输入输出的object文件格式
        [-I bfdname|--input-target=bfdname] 输入object的文件格式
        [-O bfdname|--output-target=bfdname] 输出目标的格式
        [-B bfdarch|--binary-architecture=bfdarch] 输入是架构无关的bfd中间格式
        [-S|--strip-all]
        [-g|--strip-debug]
        [--strip-unneeded]
        [-K symbolname|--keep-symbol=symbolname]
        [--keep-file-symbols]
        [--keep-section-symbols]
        [-N symbolname|--strip-symbol=symbolname]
        [--strip-unneeded-symbol=symbolname]
        [-G symbolname|--keep-global-symbol=symbolname]
        [--localize-hidden]
        [-L symbolname|--localize-symbol=symbolname]
        [--globalize-symbol=symbolname]
        [--globalize-symbols=filename]
        [-W symbolname|--weaken-symbol=symbolname]
        [-w|--wildcard]
        [-x|--discard-all]
        [-X|--discard-locals]
        [-b byte|--byte=byte]
        [-i [breadth]|--interleave[=breadth]]
        [--interleave-width=width]
        [-j sectionpattern|--only-section=sectionpattern]
        [-R sectionpattern|--remove-section=sectionpattern]
        [--keep-section=sectionpattern]
        [--remove-relocations=sectionpattern]
        [--strip-section-headers]
        [-p|--preserve-dates]
        [-D|--enable-deterministic-archives]
        [-U|--disable-deterministic-archives]
        [--debugging]
        [--gap-fill=val]
        [--pad-to=address]
        [--set-start=val]
        [--adjust-start=incr]
        [--change-addresses=incr]
        [--change-section-address sectionpattern{=,+,-}val]
        [--change-section-lma sectionpattern{=,+,-}val]
        [--change-section-vma sectionpattern{=,+,-}val]
        [--change-warnings] [--no-change-warnings]
        [--set-section-flags sectionpattern=flags]
        [--set-section-alignment sectionpattern=align]
        [--add-section sectionname=filename]
        [--dump-section sectionname=filename]
        [--update-section sectionname=filename]
        [--rename-section oldname=newname[,flags]]
        [--long-section-names {enable,disable,keep}]
        [--change-leading-char] [--remove-leading-char]
        [--reverse-bytes=num]
        [--srec-len=ival] [--srec-forceS3]
        [--redefine-sym old=new]
        [--redefine-syms=filename]
        [--weaken]
        [--keep-symbols=filename]
        [--strip-symbols=filename]
        [--strip-unneeded-symbols=filename]
        [--keep-global-symbols=filename]
        [--localize-symbols=filename]
        [--weaken-symbols=filename]
        [--add-symbol name=[section:]value[,flags]]
        [--alt-machine-code=index]
        [--prefix-symbols=string]
        [--prefix-sections=string]
        [--prefix-alloc-sections=string]
        [--add-gnu-debuglink=path-to-file]
        [--only-keep-debug]
        [--strip-dwo]
        [--extract-dwo]
        [--extract-symbol]
        [--writable-text]
        [--readonly-text]
        [--pure]
        [--impure]
        [--file-alignment=num]
        [--heap=size]
        [--image-base=address]
        [--section-alignment=num]
        [--stack=size]
        [--subsystem=which:major.minor]
        [--compress-debug-sections]
        [--decompress-debug-sections]
        [--elf-stt-common=val]
        [--merge-notes]
        [--no-merge-notes]
        [--verilog-data-width=val]
        [-v|--verbose]
        [-V|--version]
        [--help] [--info]
        infile [outfile] 输入文件(可选：输出文件)
```
