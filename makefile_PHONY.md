###.PHONY makefile中的伪目标
当前目录中只有一个hello.c, 于是用makefile来管理,

写了一个如下简单的makefile文件:

        $(CC) = gcc

        all:hello

        hello:hello.c
            $(CC) -o $@ $<

        clean:
            rm hello

执行make之后生成可执行文件(hello)

执行make clean，这样就删除了该可执行文件

如果此时在当前目录下建立一个clean的文件，执行

        make

        make clean

就会出现`make: `clean' is up to date.`的提示，并且hello文件并

没有被删除

这时就可以用.PHONY定义伪目标来解决上述问题

        $(CC) = gcc

        all:hello

        hello:hello.c
            $(CC) -o $@ $<

        .PHONY:clean

        clean:
            rm hello

此时执行`make clean` 就可以删除掉hello文件

伪目标可以解决的问题:
    1. 如上，为了避免在makefile中定义的只执行命令的目标

        和工作目录下的实际文件出现名字冲突

    2. 另一种是提交执行makefile时的效率
