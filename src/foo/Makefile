# Makefile for subdir

# build shared library with -fPIC, -shared
CFLAGS    = -fPIC # -g -O3 # CXXFLAGS for .cpp
CPPFLAGS  = -MMD -MP # -I../bar
LDFLAGS   = -shared # -L../bar
LDLIBS    = # -lbar
#CC       = $(CXX) # link with CXX for .cpp

LDFLAGS  += -Wl,-rpath,'$$ORIGIN/../bar'
LDFLAGS  += -Wl,-rpath,'$$ORIGIN/../lib'
LDFLAGS  += -Wl,-soname,$(soname)

# make # NDEBUG=1
ifdef NDEBUG
CFLAGS   += -O3 # .cpp
CPPFLAGS += -DNDEBUG
else
CFLAGS   += -g # .cpp
LDFLAGS  += -fsanitize=address
endif

all : foo # bar

# target name is basename of one of the source files
foo : $(patsubst %.c,%.o,$(wildcard *.c)) # .cpp
#bar : $(patsubst %.c,%.o,bar.c) # .cpp
-include *.d
clean : ; -rm -fr *.o *.d foo *.so*
.PHONY : all clean
