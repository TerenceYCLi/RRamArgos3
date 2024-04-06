# RRamArgos3
Duplicate the simulation environment for the ReRam simulation using Argos 3

https://github.com/Pold87/blockchain-swarm-robotics

https://github.com/ilpincy/argos3/tree/master

https://github.com/demiurge-project/argos3-epuck

https://github.com/Pold87/AB-interface-Blockchain-module

https://github.com/Pold87/AB-interface-ARGoS-module

# Install Argos3
## install the dependencies for Ubuntu 22.04
```
sudo apt-get install cmake libfreeimage-dev libfreeimageplus-dev \
  qt5- freeglut3-dev libxi-dev libxmu-dev liblua5.3-dev \
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

# Install Argos3-epuck
```
git clone https://github.com/demiurge-project/argos3-epuck argos3-epuck
```

```
cd argos3-epuck
mkdir build
cd build
cmake ../src
make
sudo make install
```
