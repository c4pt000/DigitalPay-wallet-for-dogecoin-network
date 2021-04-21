# Dogecoin Core [DOGE, Ð]

requires docker

docker run -it -d --net=host -v /opt/host-opt:/opt/host-opt -v /sys/fs/cgroup:/sys/fs/cgroup:ro -e "DISPLAY=${DISPLAY:-:0.0}" -v /tmp/.X11-unix:/tmp/.X11-unix -v /root/.Xauthority:/root/.Xauthority c4pt/dogesnap-wallet bash

15333cbbf51596c2868fe45d045d3f33839275dcc419519267aeb59335e657ef

(once loaded)
docker commit <docker_vm_hash>

docker ps -a

# backup wallet copy from /dogecoin-datadir/wallet.dat to /opt/host-opt/wallet.dat

![Dogecoin](https://raw.githubusercontent.com/c4pt000/dogecoin-frontend-edit/main/my-doge-deposit.png)

[![Build Status](https://travis-ci.com/dogecoin/dogecoin.svg?branch=master)](https://travis-ci.com/dogecoin/dogecoin)

