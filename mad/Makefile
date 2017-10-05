include ../Makefile.inc
include ../mibench.mk

all: mad

CC=$(RUMPRUN_CC)
CXX=$(RUMPRUN_CXX)
export CC CXX

build/.stamp: | dl/${MIBENCH_CONSUMER}
	mkdir -p $(dir $@)
	(cd build && tar -xz --strip-components 2 -f ../dl/${MIBENCH_CONSUMER} consumer/mad)
	touch $@

build/mad-0.14.2b/Makefile: build/.stamp
	(cd $(dir $@) && ./configure --host=$(RUMPRUN_TOOLCHAIN_TUPLE);)

mad: build/mad-0.14.2b/Makefile
	(cd $(dir $^) && make)

.PHONY: clean
clean:
	rm -rf build
