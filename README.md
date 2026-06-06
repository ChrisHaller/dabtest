# Test DAB+ Transmitter with a Raspi 5 and a HackRF

## Build odr-mmbtools


```

sudo apt-get install --yes build-essential automake libtool
sudo apt-get install --yes libzmq3-dev libzmq5
sudo apt-get install --yes libasound2-dev
sudo apt-get install --yes libjack-jackd2-dev
sudo apt-get install --yes vlc libvlc-dev
sudo apt-get install --yes libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev
sudo apt-get install --yes libcurl4-openssl-dev

sudo apt-get install --yes libboost-dev

sudo apt-get install --yes libsoapysdr-dev
sudo apt-get install --yes libfftw3-dev
sudo apt install soapysdr-module-hackrf hackrf
sudo apt install libsoapysdr-dev


mkdir ~/odr
cd ~/odr
git clone https://github.com/Opendigitalradio/ODR-AudioEnc.git
cd ODR-AudioEnc
./bootstrap
./configure --enable-alsa --enable-jack --enable-vlc --enable-gst
make
sudo make install


cd ~/odr
git clone https://github.com/Opendigitalradio/ODR-DabMux.git
cd ODR-DabMux
./bootstrap.sh
./configure
make
sudo make install


cd ~/odr
git clone https://github.com/Opendigitalradio/ODR-DabMod.git
cd ODR-DabMod
./bootstrap.sh
./configure --disable-output-uhd
make
sudo make install

```

## for PlutoSDR instead of HackRF (optional)
cd ~/odr
git clone https://github.com/pothosware/SoapyPlutoSDR
cd SoapyPlutoSDR
mkdir build && cd build
cmake ..
make
sudo make install
sudo ldconfig


## Transmission

- Connect HackRF to a dummyload
- odr-dabmod
- odr-dabmux
- odr-audioenc


