# Dogecoin Core [DOGE, Ð]
![s1](https://raw.githubusercontent.com/c4pt000/dogecoin/main/dogecoin-loading-splash.png)

![s1](https://raw.githubusercontent.com/c4pt000/dogecoin/main/dogecoin-main-window.png)

![s1](https://raw.githubusercontent.com/c4pt000/dogecoin/main/dogecoin-frontend-edit.png)

# requires ports 22555 and 22556

* updates every 1-2 hours from a private docker repo as a distribution point to keep blockchain for dogecoin synced to end user client of dogecoin-qt


to mount the blockchain on the host from docker

```
docker run -it -d --net=host -v /opt/dogecoin-blockchain:/opt/dogecoin-datadir/ -v /sys/fs/cgroup:/sys/fs/cgroup:ro -e "DISPLAY=${DISPLAY:-:0.0}" -v /tmp/.X11-unix:/tmp/.X11-unix -v /root/.Xauthority:/root/.Xauthority c4pt/dogesnap-wallet bash &

cp -rf /dogecoin-datadir/* /opt/dogecoin-blockchain
```

# requires docker dogecoin-qt 
```
docker run -it -d --net=host -v /opt/host-opt:/opt/host-opt -v /sys/fs/cgroup:/sys/fs/cgroup:ro -e "DISPLAY=${DISPLAY:-:0.0}" -v /tmp/.X11-unix:/tmp/.X11-unix -v /root/.Xauthority:/root/.Xauthority c4pt/dogesnap-wallet bash
```
15333cbbf51596c2868fe45d045d3f33839275dcc419519267aeb59335e657ef

(once loaded)
docker commit <docker_vm_hash>

docker ps -a

# backup wallet copy from /dogecoin-datadir/wallet.dat to /opt/host-opt/wallet.dat
```
docker exec -it 15333cbbf51596c2868fe45d045d3f33839275dcc419519267aeb59335e657ef bash
crtl-C to drop to prompt
```

# source build (fedora 34)
```

 yum groupinstall "C Development Tools and Libraries" -y
 yum install git-core libdb-cxx-devel libdb-cxx openssl-devel libevent-devel java-11-openjdk-devel cppzmq-devel \
 qrencode-devel qt5-qtbase-devel.x86_64 qt5-linguist-5.15.2-5.fc34.x86_64 protobuf-devel opencv-devel.x86_64 \
 opencv-devel-4.5.2-1.fc34.x86_64 cargo boost-devel miniupnpc-devel.x86_64 diffutils -y

cp -rf /usr/include/opencv4/opencv2 /usr/include/

cd /opt

git clone https://github.com/c4pt000/dogecoin

cd dogecoin

sh autogen.sh

./configure --prefix=/usr --with-incompatible-bdb


you might get a warning here
configure: WARNING: Found Berkeley DB other than 5.1; wallets opened by this build will not be portable!
due to libdb-cxx being 5.3 

make -j24                              if your system has 24 cores for faster builds
make -j24 install


```

![Dogecoin](https://raw.githubusercontent.com/c4pt000/dogecoin-frontend-edit/main/my-doge-deposit.png)

[![Build Status](https://travis-ci.com/dogecoin/dogecoin.svg?branch=master)](https://travis-ci.com/dogecoin/dogecoin)

