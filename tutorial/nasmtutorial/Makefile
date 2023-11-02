SRC = ${wildcard src/*.asm}
OBJ = ${patsubst src/%.asm,obj/%.o, ${SRC}}
BIN = hello

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

${OBJ}: ${SRC} obj
	nasm -felf64 -o $@ $<

${BIN}: ${OBJ}
	ld -o $@ $<

obj/hello.o: src/hello.asm
hello: obj/hello.o


.PHONY: all clean
