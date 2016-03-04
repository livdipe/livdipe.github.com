###.PHONY makefile中的伪目标
> 当前目录中只有一个hello.c, 于是用makefile来管理,
> 写了一个如下简单的makefile文件:
        $(CC) = gcc

        all:hello

        hello:hello.c
            $(CC) -o $@ $<
        clean:
            rm hello
