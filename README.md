# HyperledgerFabricDeploy
记录在云上部署HyperledgerFabric过程

OS：ubuntu 16
docker已安装成功
go已安装成功

step  1 修改 docker镜像为国内：
修改 /etc/docker/daemon.json 文件并添加上 registry-mirrors 键值。
cd /etc/docker/
touch daemon.json //创建daemon.json文件
$ sudo vi /etc/docker/daemon.json 
{
 "registry-mirrors": ["https://registry.docker-cn.com"]
}

step2：下载docker镜像
sudo docker pull hyperledger/composer-playground:0.18.3-20180322140240
sudo docker pull hyperledger/hyperledger/fabric-peer:x86_64-1.1.0
sudo docker pull hyperledger/fabric-couchdb:x86_64-1.0.6
sudo docker pull hyperledger/fabric-zookeeper:x86_64-1.0.6
sudo docker pull hyperledger/fabric-kafka:x86_64-1.0.6
sudo docker pull hyperledger/fabric-membersrvc


step3：修改docker镜像的tag
sudo docker tag b34be29aa084 docker.io/hyperledger/composer-playground:hf20180323
sudo docker tag b023f9be0771 docker.io/hyperledger/fabric-peer:hf20180323
sudo docker tag 380446aa57b6 docker.io/hyperledger/fabric-couchdb:hf20180323
sudo docker tag 4e726a9527ec docker.io/hyperledger/fabric-kafka:hf20180323
sudo docker tag 205a873eee5d docker.io/hyperledger/fabric-zookeeper:hf20180323

#如果需要删除指定Image ID的镜像 docker rmi <image id>
#sudo docker rmi hyperledger/composer-zookeeper:hf20180323

step4: 加载这些镜像文件
sudo docker load hyperledger/composer-playground:hf20180323
sudo docker load hyperledger/fabric-peer:hf20180323
sudo docker load hyperledger/composer-couchdb:hf20180323
sudo docker load hyperledger/fabric-kafka:hf20180323
sudo docker load hyperledger/fabric-zookeeper:hf20180323

