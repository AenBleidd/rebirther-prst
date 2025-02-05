# Makefile for Linux

EXE       = prst
LIB_GWNUM = ../../framework/gwnum/mac64/gwnum.a

COMPOBJS_COMMON = md5.o arithmetic.o group.o giant.o lucas.o config.o inputnum.o integer.o logging.o file.o task.o exp.o fermat.o order.o pocklington.o morrison.o proof.o testing.o support.o
COMPOBJS        = $(COMPOBJS_COMMON) prst.o

# Source directories

VPATH     = ..:../../framework:../../framework/arithmetic
SDKPATH=`xcodebuild -version -sdk macosx Path`

# See README.md for how to get macOS SDK
LFLAGS    = -Wl,-syslibroot,${SDKPATH},-arch,x86_64 -lm -lpthread -lstdc++ -L$(VCPKG_DIR)/lib -lgmp

DUMMY2    =

#CC        = /usr/local/bin/gcc-12 -mmacosx-version-min=10.9
#CC        = /usr/local/bin/gcc-12
#CXX       = /usr/local/bin/g++-12
CC = `xcrun -find gcc`
CXX = `xcrun -find g++`
CFLAGS    = -arch x86_64 -mmacosx-version-min=10.13 -isysroot ${SDKPATH} -I/usr/local/include/ -I.. -I../../framework/gwnum -I$(VCPKG_DIR)/include/ -DGMP -DX86_64 -O2 -std=c99     -Wall -Wextra
CXXFLAGS  = -arch x86_64 -mmacosx-version-min=10.13 -isysroot ${SDKPATH} -I/usr/local/include/ -I.. -I../../framework -I../../framework/arithmetic -I../../framework/gwnum -I$(VCPKG_DIR)/include/ -DGMP -DX86_64 -O2 -std=gnu++17 -Wall -Wextra -no-pie

# the code is too noisy for all warnings
CXXFLAGS += -Wno-sign-compare

#########################################################################

all: $(EXE)

$(EXE): $(COMPOBJS)
	$(CXX) $(LFLAGS) -o $@ $(COMPOBJS) $(LIB_GWNUM)

clean:
	rm -f $(EXE) $(COMPOBJS)
