include Make.inc
#include Make_msys2.inc
#include Make_osx.inc

CXXFLAGS = -std=c++11 -fPIC
ifdef DEBUG
CXXFLAGS += -g -O0 -Wall -fbounds-check -pedantic -D_GLIBCXX_DEBUG
else
CXXFLAGS += -O3 -march=native -Wall
endif

default:	help

all:	HelloWorld.exe Circulation_jeton.exe Calcul_de_pi.exe Diffusion_hypercube.exe

HelloWorld.exe:	HelloWorld.cpp
	$(CXX) $(CXXFLAGS) -o HelloWorld.exe HelloWorld.cpp $(LIB)

Circulation_jeton.exe:	Circulation_jeton.cpp
	$(CXX) $(CXXFLAGS) -o Circulation_jeton.exe Circulation_jeton.cpp $(LIB)

Calcul_de_pi.exe:	Calcul_de_pi.cpp
	$(CXX) $(CXXFLAGS) -o Calcul_de_pi.exe Calcul_de_pi.cpp $(LIB)

Diffusion_hypercube.exe:	Diffusion_hypercube.cpp
	$(CXX) $(CXXFLAGS) -o Diffusion_hypercube.exe Diffusion_hypercube.cpp $(LIB)

SkeletonMPIProgramWithFilesOutput.exe:	SkeletonMPIProgramWithFilesOutput.cpp
	$(CXX) $(CXXFLAGS) -o SkeletonMPIProgramWithFilesOutput.exe SkeletonMPIProgramWithFilesOutput.cpp $(LIB)

SkeletonMPIProgram.exe:	SkeletonMPIProgram.cpp
	$(CXX) $(CXXFLAGS) -o SkeletonMPIProgram.exe SkeletonMPIProgram.cpp $(LIB)

HelloWorld: HelloWorld.exe
	mpiexec $(MPIOPT) -np 16 ./HelloWorld.exe

SkeletonMPIProgramWithFilesOutput: SkeletonMPIProgramWithFilesOutput.exe
	mpiexec $(MPIOPT) -np 16 ./SkeletonMPIProgram.exe

SkeletonMPIProgram: SkeletonMPIProgram.exe
	mpiexec $(MPIOPT) -np 16 ./SkeletonMPIProgram.exe

Circulation_jeton: Circulation_jeton.exe
	mpiexec $(MPIOPT) -np 16 ./Circulation_jeton.exe

Calcul_de_pi: Calcul_de_pi.exe
	mpiexec $(MPIOPT) -np 5 ./Calcul_de_pi.exe

Diffusion_hypercube: Diffusion_hypercube.exe
	mpiexec $(MPIOPT) -np 16 ./Diffusion_hypercube.exe

help: 
	@echo "Available targets : "
	@echo "    all                      : compile all executables"
	@echo "    HelloWorld.exe           : compile HelloWorld executable"
	@echo "    Circulation_jeton.exe    : compile Circulation_jeton executable"
	@echo "    Calcul_de_pi.exe         : compile Calcul_de_pi executable"
	@echo "    Diffusion_hypercube.exe  : compile Diffusion_hypercube executable"
	@echo "Add DEBUG=yes to compile in debug"
	@echo "Configuration :"
	@echo "    CXX      :    $(CXX)"
	@echo "    CXXFLAGS :    $(CXXFLAGS)"

clean:
	@rm -f *.exe *~ 

