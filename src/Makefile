CC    = gcc# C compiler
LC    = flex# Lex compiler
YC    = bison# Yacc compiler
DEBUG = 0# Debugging flag, level 0, 1, 2, 3
CCF   = -Wall -DDEBUG=$(DEBUG)# C compiler flag
YCF   = -dy# Yacc compiler flag
LL    = -ll -ly# link lib
LT    = Scanner# Lex target
YT    = Parser# Yacc target
LEX   = lex.yy# Lex output
YACC  = y.tab# Yacc output
STT   = SymbolTable/SymbolTable# Symbol table target
EXEC  = JavaParser

ifeq ($(DEBUG), 3) 
	YCF = -dtvy
endif

.PHONY: all
all: clean $(LEX).c $(YACC).c $(STT).c
	$(CC) $(CCF) $(YACC).c $(STT).c -o $(EXEC)
	rm -f $(LEX).c $(YACC).*

$(LEX).c: $(LT).l $(YACC).h
	$(LC) $(LT).l

$(YACC).h: $(YT).y
	$(YC) $(YCF) $(YT).y

.PHONY: clean
clean:
	rm -f $(EXEC) $(LEX).c $(YACC).* y.output

