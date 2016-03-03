# Compile

wget http://repository.timesys.com/buildsources/e/eglibc/eglibc-2.14-14285/eglibc-2.14-14285.tar.gz
tar xvf eglibc-2.14-14285.tar.gz
cd eglibc-2.14-14285/
sudo apt-get install gawk -y

mkdir build
cd build
../configure --prefix=/home/gavin/opt/eglibc
make
make install

LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/eglibc/lib make package/compile V=s
