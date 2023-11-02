SRC = ${wildcard src/*.asm}
OBJ = ${patsubst src/%.asm,obj/%.o, ${SRC}}
BIN = hello triangle hola

all: ${BIN}
	@echo all built

options:
	@echo "SRC: ${SRC}"
	@echo "OBJ: ${OBJ}"
	@echo "BIN: ${BIN}"

clean:
	@rm -rf ${BIN} obj

obj:
	mkdir -p obj

obj/%.o: src/%.asm obj
	nasm -felf64 -o $@ $<

${BIN}:
	ld -o $@ $<

obj/hello.o: src/hello.asm
hello: obj/hello.o

obj/triangle.o: src/triangle.asm
triangle: obj/triangle.o

obj/hola.o: src/hola.asm
hola: obj/hola.o
	gcc -no-pie -z noexecstack -o $@ $<

.PHONY: all clean
