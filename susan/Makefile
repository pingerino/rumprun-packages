include ../Makefile.inc
include ../mibench.mk

all: susan

build/.stamp: | dl/${MIBENCH_AUTOMOTIVE}
	mkdir -p $(dir $@)
	(cd build && tar -xz --strip-components 2 -f ../dl/${MIBENCH_AUTOMOTIVE} automotive/susan)
	touch $@

data: build/.stamp
	mkdir -p $@
	cp build/input_small.pgm $@/
	cp build/input_large.pgm $@/

susan: data
	(cd build; ${RUMPRUN_CC} -osusan.o susan.c -lm -lc -g)

.PHONY: clean

clean:
	rm -rf build
