ifndef EXEDIR
EXEDIR = ~/.local/bin
endif
ifndef LIBDIR
EXEDIR = ~/.local/lib
endif
ifndef EXENAME
EXENAME = hfk
endif

CC := g++
ifeq ($(shell uname -s),Darwin)
CFLAGS := -std=c++11 -O3 -g -mmacosx-version-min=10.9
else
CFLAGS := -std=c++11 -O3 -g -fPIC
endif

.PHONY: all install uninstall clean

HDR := Alg.h Diagrams.h
SRC := Main.cpp \
       Utility.cpp \
       Min.cpp \
       Max.cpp \
       Crossing.cpp \
       Simplify.cpp \
       HomologyRank.cpp \
       Report.cpp \
       Diagrams.cpp \
       KnotFloer.cpp
OBJ := $(SRC:.cpp=.o)
SO := Utility.o \
      Min.o \
      Max.o \
      Crossing.o \
      Simplify.o \
      HomologyRank.o \
      Report.o \
      Diagrams.o \
      KnotFloer.o

all: $(HDR) $(OBJ)
	$(CC) $(CFLAGS) $(OBJ)

lib:
	$(CC) -shared -o libhfk.so $(CFLAGS) $(SRC)

install: all
	mkdir -p $(EXEDIR)
	install a.out $(EXEDIR)/$(EXENAME)

uninstall:
	rm -f $(EXEDIR)/$(EXENAME)

clean:
	rm *.out $(OBJ)
