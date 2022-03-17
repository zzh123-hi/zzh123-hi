- 👋 Hi, I’m @zzh123-hi
- 👀 I’m interested in ...
- 🌱 I’m currently learning 此教程如何用docker搭建AptosFullNode

[1.Aptos开发者测试申请表]https://aptos.typeform.com/to/jwSOZbH6
[2.discord链接]https://discord.gg/qeCK766G
[3.官方文档]https://aptoslabs.com/developers/
1. 配置
最低配置:

CPU: 2 核 内存: 4GiB RAM

推荐配置:

CPU: Intel Xeon Skylake or newer, 4 核 内存: 8GiB RAM

2. 逐步搭建
第一步、安装screen和docker

sudo apt install screen

screen -S homepage

sudo apt update

sudo apt install ca-certificates curl gnupg lsb-release wget -y

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update

sudo apt install docker-ce docker-ce-cli containerd.io -y

第二步，安装Docker Compose

mkdir -p ~/.docker/cli-plugins/

考虑到有些机器是国内网，docker-compose的源改了一下：

curl -L https://get.daocloud.io/docker/compose/releases/download/1.29.2/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose

chmod +x /usr/local/bin/docker-compose

docker-compose --version
chmod +x ~/.docker/cli-plugins/docker-compose

sudo chown $USER /var/run/docker.sock

第三步、创建一个文件夹 Aptos，下载配置文件

mkdir $HOME/aptos

cd $HOME/aptos

wget https://raw.githubusercontent.com/aptos-labs/aptos-core/main/docker/compose/public_full_node/docker-compose.yaml

wget https://raw.githubusercontent.com/aptos-labs/aptos-core/main/docker/compose/public_full_node/public_full_node.yaml

wget https://devnet.aptoslabs.com/genesis.blob

wget https://devnet.aptoslabs.com/waypoint.txt

第四步、启动节点

docker compose up -d

**成功！节点启动完成！

有用的代码：

检查同步状态

curl 127.0.0.1:9101/metrics 2> /dev/null | grep aptos_state_sync_version | grep type

查看日志

docker logs -f aptos-fullnode-1 --tail 5000..
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
zzh123-hi/zzh123-hi is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
