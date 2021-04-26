# seperation for blockchain data and digitalpay-client





sync every 30 minutes
see /usr/bin/digitalpay-daemon

```
mkdir /opt/blockchain               ( if it not currently in root )

docker run -it -d --net=host -v /opt/blockchain:/opt/blockchain c4pt/digitalpay-blockchain digitalpay-daemon &

docker run -it -d -v /opt/blockchain:/opt/blockchain-data c4pt/digitalpay-wallet dogecoin-qt &
```


for QR fix see
https://github.com/c4pt000/docker-DigitalPay-autosync/blob/main/src/qt/guiutil.cpp

android app in progress in current review

![s1](https://raw.githubusercontent.com/c4pt000/docker-DigitalPay-autosync/main/QR-fix.png)

![s1](https://raw.githubusercontent.com/c4pt000/docker-DigitalPay-autosync/main/android-app.receive-by-QR.png)

for electrum as a server node (WIP template only)

https://github.com/c4pt000/electrum-wallet-for-dogecoin-WIP


# DigitalPay [DOGE, Ð]

# size of synced wallet -> 3.57 GB


![s1](https://raw.githubusercontent.com/c4pt000/docker-DigitalPay-autosync/main/DigitalPay-splash.png)

![s1](https://raw.githubusercontent.com/c4pt000/docker-DigitalPay-autosync/main/DigitalPay-about.png)

![s1](https://raw.githubusercontent.com/c4pt000/docker-DigitalPay-autosync/main/DigitalPay-main-gui.png)

# requires ports 22555 and 22556

* updates every 1-2 hours from a private docker repo as a distribution point to keep blockchain for dogecoin synced to end user client of dogecoin-qt


# requires docker run -it on a fresh pull

```
docker run -it c4pt/dogesnap-wallet
```

linux to mount the blockchain on the host from docker

```
docker run -it -d --net=host -v /opt/dogecoin-blockchain:/opt/dogecoin-datadir/ -v /sys/fs/cgroup:/sys/fs/cgroup:ro -e "DISPLAY=${DISPLAY:-:0.0}" -v /tmp/.X11-unix:/tmp/.X11-unix -v /root/.Xauthority:/root/.Xauthority c4pt/dogesnap-wallet bash &

15333cbbf51596c2868fe45d045d3f33839275dcc419519267aeb59335e657ef <- a docker vm hash

docker exec -it 15333cbbf51596c2868fe45d045d3f33839275dcc419519267aeb59335e657ef bash


cp -rf /dogecoin-datadir/* /opt/dogecoin-blockchain
```

# requires docker dogecoin-qt  linux
```
docker run -it -d --net=host -v /opt/host-opt:/opt/host-opt -v /sys/fs/cgroup:/sys/fs/cgroup:ro -e "DISPLAY=${DISPLAY:-:0.0}" -v /tmp/.X11-unix:/tmp/.X11-unix -v /root/.Xauthority:/root/.Xauthority c4pt/dogesnap-wallet dogecoin-qt &

15333cbbf51596c2868fe45d045d3f33839275dcc419519267aeb59335e657ef <- a docker vm hash

docker exec -it 15333cbbf51596c2868fe45d045d3f33839275dcc419519267aeb59335e657ef bash


(once loaded)
backup wallet copy from /dogecoin-datadir/wallet.dat to /opt/host-opt/wallet.dat

(once loaded) from another terminal to commit changes
docker commit <docker_vm_hash>

docker ps -a

```




# windows docker host
![s1](https://res.cloudinary.com/practicaldev/image/fetch/s--1fOShFRZ--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.amazonaws.com/i/3eh1lry7125modpdj6a2.png)


```
https://dev.to/darksmile92/run-gui-app-in-linux-docker-container-on-windows-host-4kde

https://chocolatey.org/

choco install vcxsrv

run Xlaunch from the start menu 


(enable "disable access control")

open -> powershell

ipconfig    (get LAN ip)
                                  
set-variable -name DISPLAY -value 192.168.xxx.xx:0.0      <- replace with your LAN ip
docker run -it c4pt/dogesnap-wallet

docker run -it -d  --net=host --privileged -v C:/opt/host-opt:/opt/host-opt -e DISPLAY=$DISPLAY c4pt/dogesnap-wallet

docker exec -it <docker_vm_hash> bash

dogecoin-qt &

(once wallet is loaded)
backup wallet.dat 
copy wallet.dat -> /opt/host-opt in guest to backup your wallet

wallet.dat will be located in C:\opt\host-opt on host 

cp /dogecoin-datadir/wallet.dat /opt/host-opt

from another powershell
docker commit <docker_vm_hash>



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

