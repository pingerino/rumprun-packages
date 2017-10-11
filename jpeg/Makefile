include ../Makefile.inc
include ../mibench.mk

all: jpeg

export RUMPRUN_CC

build/.stamp: | dl/${MIBENCH_CONSUMER}
	mkdir -p $(dir $@)
	(cd build && tar -xz --strip-components 2 -f ../dl/${MIBENCH_CONSUMER} consumer/jpeg)
	(cd build && ../../scripts/apply-patches.sh ./ ../patches/*)
	touch $@

jpeg: build/.stamp
	(cd build/jpeg-6a; make)

.PHONY: clean

clean:
	rm -rf build
