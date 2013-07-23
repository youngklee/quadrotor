# This Makefile was tested with GNU Make
CXX=g++

# Use pkg-config to lookup the proper compiler and linker flags for LCM
CFLAGS=`pkg-config --cflags lcm`
LDFLAGS=`pkg-config --libs lcm`

msg_types=*.lcm

all: exlcm/altitude_t.hpp exlcm/altitude_list_t.hpp \
	sonar_lcm

sonar_lcm: sonar_lcm.o 
	$(CXX) -o $@ $^ $(LDFLAGS)

%.o: %.cpp exlcm/altitude_t.hpp
	$(CXX) $(CFLAGS) -I. -o $@ -c $< 

exlcm/%.hpp:
	lcm-gen -x *.lcm

clean:
	rm -f sonar_lcm
	rm -f *.o exlcm/*.o
	rm -f exlcm/*.hpp
