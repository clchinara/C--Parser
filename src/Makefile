TARGET = parser
OBJECT = parser.tab.c parser.tab.o lex.yy.c alloc.o functions.o
CC = gcc -g
LEX = flex
YACC = bison -v
YACCFLAG = -d
LIBS = -ll 

parser: parser.tab.o alloc.o functions.o
	$(CC) -o $(TARGET) parser.tab.o alloc.o functions.o $(LIBS)

parser.tab.o: parser.tab.c lex.yy.c alloc.o functions.c
	$(CC) -c parser.tab.c
    
lex.yy.c: lexer.l
	$(LEX) lexer.l

parser.tab.c: parser.y 
	$(YACC) $(YACCFLAG) parser.y

alloc.o: alloc.c
	$(CC) -c alloc.c
	
functions.o: functions.c
	$(CC) -c functions.c

clean:
	rm -f $(TARGET) $(OBJECT) 

parse:
	./parser ../test/func.c

png:
	dot -Tpng -o out.png AST_Graph.gv
