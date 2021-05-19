# 将程序编译为WebAssembly

您可以先使用clang进行编译，然后使用wasm-ld进行链接，以将C程序编译为作为WebAssembly模块运行。 根据所使用的操作系统和Clang版本，您可能会使用其他版本的WebAssembly链接器，例如macOS上的wasm-ld或Debian上的wasm-ld-8。

在macOS上编译为WebAssembly：

1. 通过运行以下clang命令来编译程序：

**`clang --target=wasm32 -c -O3 reverse.c`**

    2. 通过运行以下wasm-ld命令，运行链接器以创建WebAssembly模块：

**`wasm-ld --no-entry --export-dynamic --allow-undefined reverse.o -o reverse.wasm`**

