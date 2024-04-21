# new readme to install the demo in Ubuntu 22.04/20.04

# download the sources
```
cd ~/
mkdir ReRam
cd ReRam
git clone https://github.com/Pold87/blockchain-swarm-robotics
```

## install the dependencies for Ubuntu 22.04
```
sudo apt-get install cmake libfreeimage-dev libfreeimageplus-dev \
  qtbase5-dev qt5-qmake freeglut3-dev libxi-dev libxmu-dev liblua5.3-dev \
  lua5.3 doxygen graphviz libgraphviz-dev asciidoc
```

# install Argos by using the install script in blockchain-swarm-robotics
```
cd blockchain-swarm-robotics/scripts
bash install_argos.sh
```
## copy below into the end of ~/.bashrc
```
source $HOME/argos3-dist/bin/setup_argos3
```

# install geth
## install go1.7.3
```
cd ~/
wget https://go.dev/dl/go1.7.3.linux-amd64.tar.gz
tar xvf go1.7.3.linux-amd64.tar.gz
vim ~/.bashrc
```
## copy below into the end of ~/.bashrc
```
# go 1.7.3
export GOROOT=$HOME/go
export PATH=$PATH:$GOROOT/bin
```
## restart a new prompt then enter
```
go version
```
the version of go should 1.7.3, if not, uninstall the system golan by 
```
sudo apt remove golang*
```
## install geth by running 
```
cd ~/ReRam/blockchain-swarm-robotics
bash create_geths.sh
```
## after installation, add below to the end of ~/.bashrc
```
export PATH=$PATH:$HOME/ReRam/blockchain-swarm-robotics/go-ethereum0/build/bin
```

# install solc, since the version in repo is v0.4.8, need to build from source
## install dependency libboost < 1.7.0
```
sudo apt install libboost1.67-all-dev
```

## download solc v0.4.8
```
cd ~/Downloads
git clone --recurse-submodules --depth 1 --branch v0.4.8 https://github.com/ethereum/solidity.git
cd solidity
mkdir build
cd build
cmake ..
```

## You will encounter error: this statement may fall through [-Werror=implicit-fallthrough=] 
open vscode 
open ~/Downloads/solidity/build/deps/jsoncpp/src/jsoncpp-project/CMakeLists.txt
comment line 95 set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Werror")

search -Werror through the build folder
delete all -Werror flag in **flags.make** files


