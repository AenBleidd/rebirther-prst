# Makefile for Linux

EXE       = prst
LIB_GWNUM = ../../framework/gwnum/mac64/gwnum.a

COMPOBJS_COMMON = md5.o arithmetic.o group.o giant.o lucas.o config.o inputnum.o integer.o logging.o file.o task.o exp.o fermat.o order.o pocklington.o morrison.o proof.o testing.o support.o
COMPOBJS        = $(COMPOBJS_COMMON) prst.o

# Source directories

VPATH     = ..:../../framework:../../framework/arithmetic

SDKPATH=`xcodebuild -version -sdk macosx Path`
CC        =`xcrun -find gcc`
CXX       =`xcrun -find g++`
CFLAGS    = -arch x86_64 -mmacosx-version-min=10.13 -isysroot ${SDKPATH} -I/usr/local/include/ -I.. -I../../framework/gwnum -I$(VCPKG_DIR)/include/ -DGMP -DX86_64 -O2 -std=c99 -Wall -Wextra
CXXFLAGS  = -arch x86_64 -mmacosx-version-min=10.13 -isysroot ${SDKPATH} -I/usr/local/include/ -I.. -I../../framework -I../../framework/arithmetic -I../../framework/gwnum -I$(VCPKG_DIR)/include/ -DGMP -DX86_64 -O3 -stdlib=libc++ -std=c++17 -Wall -Wextra -Wno-sign-compare
LDFLAGS    = -Wl,-syslibroot,${SDKPATH},-arch,x86_64 -lm -pthread -lstdc++ -L$(VCPKG_DIR)/lib -lgmp -static

#########################################################################

all: $(EXE)

$(EXE): $(COMPOBJS)
	$(CXX) $(LDFLAGS) -o $@ $(COMPOBJS) $(LIB_GWNUM)

clean:
	rm -f $(EXE) $(COMPOBJS)
