.PHONY: all
all: testclient testserver testadmin

libobjects = btree_int.o client_comm.o conds.o config.o data.o db_engine.o db_main.o error.o index.o memory.o parser_commands.o parser_conds.o query.o result.o server_comm.o sql_parser.o strutil.o tabconf.o tabdef.o textfileio.o

#### TARGETS - bins out
testclient: testclient.c libmydb.a #w/ the compilation # -lhistory 
	$(CC) -o testclient -L. testclient.c client_comm.c libmydb.a -lreadline 
testserver: testserver.c libmydb.a #w/ the compilation # -lhistory 
	$(CC) -o testserver -L. testserver.c server_comm.c libmydb.a -lreadline 
testadmin: testadmin.c libmydb.a #w/ the compilation # -lhistory 
	$(CC) -o testadmin -L. testadmin.c libmydb.a -lreadline 

#### TARGETS others
libmydb.a: $(libobjects)
	ar -rcvs libmydb.a $(libobjects)

#### STUFF
clean:
	-rm $(libobjects) libmydb.a testclient testserver testadmin

#### OBJ. FILES
btree_int.o: btree_int.c
	$(CC) -c $(CFLAGS) btree_int.c
client_comm.o: client_comm.c
	$(CC) -c $(CFLAGS) client_comm.c
conds.o: conds.c
	$(CC) -c $(CFLAGS) conds.c
config.o: config.c
	$(CC) -c $(CFLAGS) config.c
data.o: data.c data.h textfileio.h linklist.h	
	$(CC) -c $(CFLAGS) data.c
db_engine.o: db_engine.c
	$(CC) -c $(CFLAGS) db_engine.c
db_main.o: db_main.c
	$(CC) -c $(CFLAGS) db_main.c
error.o: error.c
	$(CC) -c $(CFLAGS) error.c
index.o: index.c
	$(CC) -c $(CFLAGS) index.c
memory.o: memory.c
	$(CC) -c $(CFLAGS) memory.c
parser_commands.o: parser_commands.c
	$(CC) -c $(CFLAGS) parser_commands.c	
parser_conds.o: parser_conds.c
	$(CC) -c $(CFLAGS) parser_conds.c	
query.o: query.c
	$(CC) -c $(CFLAGS) query.c
result.o: result.c
	$(CC) -c $(CFLAGS) result.c	
server_comm.o: server_comm.c
	$(CC) -c $(CFLAGS) server_comm.c
sql_parser.o: sql_parser.c
	$(CC) -c $(CFLAGS) sql_parser.c
strutil.o: strutil.c
	$(CC) -c $(CFLAGS) strutil.c
tabconf.o: tabconf.c
	$(CC) -c $(CFLAGS) tabconf.c
tabdef.o: tabdef.c
	$(CC) -c $(CFLAGS) tabdef.c
textfileio.o: textfileio.c
	$(CC) -c $(CFLAGS) textfileio.c