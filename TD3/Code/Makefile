include Make.inc
#include Make_msys2.inc
#include Make_osx.inc

CXXFLAGS = -std=c++11 -fPIC
ifdef DEBUG
CXXFLAGS += -g -O0 -Wall -fbounds-check -pedantic -D_GLIBCXX_DEBUG
CXXFLAGS2 = CXXFLAGS
else
CXXFLAGS2 = ${CXXFLAGS} -O2 -march=native -Wall
CXXFLAGS += -O3 -march=native -Wall
endif

ALL= dotproduct.exe dotproduct_thread.exe TestProductMatrix.exe bhudda.exe bitonic.exe

default:	help

all: $(ALL)

clean:
	@rm -fr *.o *.exe *~ *.tga

%.exe: %.cpp
	$(CXX) $(CXXFLAGS) -o $@ $^ $(LIB)

TestProductMatrix.exe : TestProductMatrix.cpp Matrix.hpp Matrix.cpp  ProdMatMat.hpp ProdMatMat.cpp
	$(CXX) $(CXXFLAGS2) -o $@ $^ $(LIB)	

bitonic.exe : bitonic.cpp Vecteur.hpp Vecteur.cpp
	$(CXX) $(CXXFLAGS) -o $@ $^ $(LIB)	

help:
	@echo "Available targets : "
	@echo "    all            : compile all executables"
	@echo "Add DEBUG=yes to compile in debug"
	@echo "Configuration :"
	@echo "    CXX      :    $(CXX)"
	@echo "    CXXFLAGS :    $(CXXFLAGS)"
