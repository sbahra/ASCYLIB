ROOT = ../..

include $(ROOT)/common/Makefile.common

BINS  = $(BINDIR)/lf-ht_rcu
PROF = $(ROOT)/src

URCU_PATH = /home/trigonak/code/urcu
LDFLAGS += -lurcu-cds  -lurcu-qsbr -lurcu-signal -lurcu
CFLAGS += -I$(URCU_PATH)/

.PHONY:	all clean

all:	main

measurements.o:
	$(CC) $(CFLAGS) -c -o $(BUILDIR)/measurements.o $(PROF)/measurements.c

ssalloc.o:
	$(CC) $(CFLAGS) -c -o $(BUILDIR)/ssalloc.o $(PROF)/ssalloc.c

test.o: $(TEST_FILE)
	$(CC) $(CFLAGS) -c -o $(BUILDIR)/test.o $(TEST_FILE)

main: 	test.o ssalloc.o measurements.o
	$(CC) $(CFLAGS) $(BUILDIR)/ssalloc.o $(BUILDIR)/measurements.o $(BUILDIR)/test.o -o $(BINS) $(LDFLAGS)

clean:
	rm -f $(BINS)
