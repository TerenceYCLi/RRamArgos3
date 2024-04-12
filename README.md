# RRamArgos3
Duplicate the simulation environment for the ReRam simulation using Argos 3

https://github.com/Pold87/blockchain-swarm-robotics

https://github.com/ilpincy/argos3/tree/master

https://github.com/demiurge-project/argos3-epuck

https://github.com/Pold87/AB-interface-Blockchain-module

https://github.com/Pold87/AB-interface-ARGoS-module

# Create ReRam directory 
```
cd ~/
mkdir ReRam
```

# Install Argos3
## install the dependencies for Ubuntu 22.04
```
sudo apt-get install cmake libfreeimage-dev libfreeimageplus-dev \
  qtbase5-dev qt5-qmake freeglut3-dev libxi-dev libxmu-dev liblua5.3-dev \
  lua5.3 doxygen graphviz libgraphviz-dev asciidoc
```

```
git clone https://github.com/ilpincy/argos3.git argos3
```
```
cd argos3
mkdir build_simulator
cd build_simulator
cmake ../src
make -j8
```
```
make doc
sudo make install
```
## add path to ~/.bashrc
```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib/argos3/
```

# Install Argos3-epuck
```
cd ~/ReRam
git clone https://github.com/demiurge-project/argos3-epuck argos3-epuck
```

```
cd argos3-epuck
mkdir build
cd build
cmake ../src
make -j8
sudo make install
```

# Install AB-interface-ARGoS-module
```
cd ReRam
git clone https://github.com/Pold87/AB-interface-ARGoS-module.git
cd AB-interface-ARGoS-module/
```
## modify the CMAKEFILES.txt for find the lib path
```
vim CMakeLists.txt
```
## Place the following to line 18-24
```
# Find the ARGoS package
# find_package(PkgConfig)
# pkg_check_modules(ARGOS REQUIRED argos3_simulator)
# set(ARGOS_PREFIX ${ARGOS_PREFIX} CACHE INTERNAL "")
set(ARGOS_PREFIX "/usr/local")
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${ARGOS_PREFIX}/share/argos3/cmake)
message(STATUS "CMAKE_MODULE_PATH = ${CMAKE_MODULE_PATH}")
set(ARGOS_LIBRARY_DIRS "/usr/local/lib/argos3")
```

```
mkdir build
cd build
cmake ..
make
```
