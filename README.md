https://dogecoin.gg/files/dogecoin-bootstrap-2021-05-09.torrent
```
git clone https://github.com/c4pt000/DigitalPay-wallet-for-dogecoin-network
cd DigitalPay-wallet-for-dogecoin-network
sh autogen.sh 
./configure --prefix=/usr --with-incompatible-bdb
make -j24
make -j24 install
checkinstall --install=no --exclude=/sys/fs/selinux
alien --scripts --to-rpm *.deb 
```

```
wget https://github.com/c4pt000/DigitalPay-wallet-for-dogecoin-network/releases/download/digitalpay/digitalpay-wallet-1.1.4.x86_64.rpm
```

```
yum install digitalpay-wallet-1.1.4.x86_64.rpm -y
```
 https://github.com/c4pt000/DigitalPay-wallet-for-dogecoin-network/releases
 
 
 
 
# must have prune=2200 in dogecoin.conf or wallet will force reindex to download entire blockchain from block height 0
* current blockchain snapshot 05-05-2021
https://drive.google.com/file/d/1ZatTBK8WaxaWFcGUCGTveOwOuGXfTB-s/view?usp=sharing







* as before wallet must be always synced with a "checkmark" like bitcoin-core in order to fully function (to leave running in the background)
* the sync goes by sometimes in a burst where 20 hours might take 20 minutes to fully sync or 30 days might take 45 minutes same as with bitcoin-qt from bitcoin-core (as long as the ports aren't blocked on the LAN side or WAN side of the firewall)


![s1](https://raw.githubusercontent.com/c4pt000/docker-DigitalPay-autosync/main/checkmark-synced.png)

* recommended send
![s1](https://raw.githubusercontent.com/c4pt000/docker-DigitalPay-autosync/main/recommend-send-1.00-DOGE.png)



still a WIP** for other clients


# macOS
# https://github.com/c4pt000/docker-DigitalPay-autosync/releases/tag/dmg

place files and dogecoin.conf here -> /Users/<USER>/Library/Application\ Support/Dogecoin/
 https://raw.githubusercontent.com/c4pt000/docker-DigitalPay-autosync/main/dogecoin.conf

 
# linux 
# https://github.com/c4pt000/docker-DigitalPay-autosync/releases/download/digitalpay/digitalpay-current-QRcodefix.tar.gz


```
(you add the blockchain data and dogecoin.conf raw binary)
tar -xvf digitalpay-current-QRcodefix.tar.gz
cd dogecoin
./src/qt/dogecoin-qt
```
# android
# https://play.google.com/store/apps/details?id=us.digitalpay.wallet

android

![s1](https://raw.githubusercontent.com/c4pt000/docker-DigitalPay-autosync/main/digitalpay-android-QR.png)

![s1](https://raw.githubusercontent.com/c4pt000/docker-DigitalPay-autosync/main/QR-app-store-install.png)


# to find this repo by QR code see also apple app store and google play suggestion 
 * https://github.com/c4pt000/Google-Play_Store_AND_Apple_App_Store_QR-codes

![s1](https://raw.githubusercontent.com/c4pt000/docker-DigitalPay-autosync/main/find-repo-by-camera-QR.png)


# seperation for blockchain data and digitalpay-client




takes 30 minutes on a first run :

# for a first run

```
mkdir /opt/blockchain
docker run -it -d --net=host -v /opt/blockchain:/opt/blockchain c4pt/digitalpay-blockchain first-run &
```

cat /usr/bin/digitalpay-daemon

```
docker run -it -d  -v /opt/blockchain:/opt/blockchain c4pt/digitalpay-blockchain digitalpay-daemon &
```


sync every 30 minutes
to run a directory sync from digitalpay-blockchain to the mounted host direcotry /opt/blockchain every 30 minutes

```
docker run -it -d  -v /opt/blockchain:/opt/blockchain c4pt/digitalpay-blockchain digitalpay-sync &
```

```

docker run -it -d --net=host -v  /opt/blockchain:/opt/blockchain  -v /sys/fs/cgroup:/sys/fs/cgroup:ro -e "DISPLAY=${DISPLAY:-:0.0}" -v /tmp/.X11-unix:/tmp/.X11-unix -v /root/.Xauthority:/root/.Xauthority c4pt/digitalpay-wallet 

docker exec -it <docker_vm_hash> bash

dogecoin-qt &


```


for QR fix see
https://github.com/c4pt000/docker-DigitalPay-autosync/blob/main/src/qt/guiutil.cpp

android app in progress in current review
![s1](https://raw.githubusercontent.com/c4pt000/docker-DigitalPay-autosync/main/digitalpay-android.png)


<br>
<br>
<br>
<br>

![s1](https://raw.githubusercontent.com/c4pt000/docker-DigitalPay-autosync/main/QR-fix.png)
<br>
<br>

![s1](https://raw.githubusercontent.com/c4pt000/docker-DigitalPay-autosync/main/android-app.receive-by-QR.png)
<br>
<br>
<br>

for electrum as a server node (WIP template only)
<br>
<br>



<br><br>
<br>
<br>
<br>
<br>
<br>

![s1](https://github.com/c4pt000/docker-DigitalPay-autosync/blob/main/Screenshot_20210426-040519.png)

<br>
<br>
<br>
<br>

![s1](https://raw.githubusercontent.com/c4pt000/docker-DigitalPay-autosync/main/Screenshot_20210426-040526.png)

<br>
<br>
<br>
<br>

# DigitalPay [DOGE, Ð]

# size of synced wallet -> 3.57 GB
```
du -h /opt/blockchain/
600M	/opt/blockchain/blocks/index
2.8G	/opt/blockchain/blocks
4.0K	/opt/blockchain/database
648M	/opt/blockchain/chainstate
3.4G	/opt/blockchain/
```


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

