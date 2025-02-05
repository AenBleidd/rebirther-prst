# Makefile for Linux

EXE       = prst
LIB_GWNUM = ../../framework/gwnum/mac64/gwnum.a

COMPOBJS_COMMON = md5.o arithmetic.o group.o giant.o lucas.o config.o inputnum.o integer.o logging.o file.o task.o exp.o fermat.o order.o pocklington.o morrison.o proof.o testing.o support.o
COMPOBJS        = $(COMPOBJS_COMMON) prst.o

# Source directories

VPATH     = ..:../../framework:../../framework/arithmetic

# See README.md for how to get macOS SDK
LFLAGS    = -syslibroot,${SDKPATH},-arch,x86_64 # -isysroot MacOSX10.7.sdk/ -mmacosx-version-min=10.7

DUMMY2    =
LIBS2     = -lm -lpthread -lstdc++ -L$(VCPKG_DIR)/lib -lgmp

#CC        = /usr/local/bin/gcc-12 -mmacosx-version-min=10.9
#CC        = /usr/local/bin/gcc-12
#CXX       = /usr/local/bin/g++-12
SDKPATH=`xcodebuild -version -sdk macosx Path`
CC = gcc -arch x86_64 -mmacosx-version-min=10.13 -isysroot ${SDKPATH} #-isysroot /Users/daohe/CLionProjects/prst/src/mac64/MacOSX10.13.sdk
CXX = g++ -arch x86_64 -mmacosx-version-min=10.13 -isysroot ${SDKPATH} #-isysroot /Users/daohe/CLionProjects/prst/src/mac64/MacOSX10.13.sdk
CFLAGS    = -I/usr/local/include/ -I.. -I../../framework/gwnum -I$(VCPKG_DIR)/include/ -DGMP -DX86_64 -O2 -std=c99     -Wall -Wextra
CXXFLAGS  = -I/usr/local/include/ -I.. -I../../framework -I../../framework/arithmetic -I../../framework/gwnum -I$(VCPKG_DIR)/include/ -DGMP -DX86_64 -O2 -std=gnu++17 -Wall -Wextra -no-pie

# the code is too noisy for all warnings
CXXFLAGS += -Wno-sign-compare

#########################################################################

all: $(EXE)

$(EXE): $(COMPOBJS)
	$(CC) $(LFLAGS) -o $@ $(COMPOBJS) $(LIB_GWNUM) $(LIBS2)

clean:
	rm -f $(EXE) $(COMPOBJS)
