CC=gcc
CFLAGS=-g -Wall

.PHONY: all

all:
	$(MAKE) -C mydb/src all

testclient:
	$(MAKE) -C mydb/src testclient	
testserver:
	$(MAKE) -C mydb/src testserver
testadmin:
	$(MAKE) -C mydb/src testadmin	

clean:
	$(MAKE) -C mydb/src clean