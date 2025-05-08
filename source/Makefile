# List of BASIC source files
BASFILES := ifftotile.bas ifftobgnd.bas lookup.bas drawborder.bas newmapedit.bas \
            ifftospec.bas invertiff.bas ifftomons.bas titlewithtext.ba game.bas viewmap.bas

# Derive .txt versions
TXTOUTPUTS := $(BASFILES:%=%.txt)

all: disk image

disk:
	c1541 -attach TOABT.D81 $(BASFILES:%=-read %)

image: $(TXTOUTPUTS)

%.bas.txt: %.bas
	petcat -65 -o $@ -- $<
%.ba.txt: %.ba
	petcat -65 -o $@ -- $<

clean:
	rm -f *.txt

xemu:
	/c/projs/xemu/build/bin/xmega65.native -hdosvirt -uartmon :4510 -8 TOABT.D81 &> /dev/null &
