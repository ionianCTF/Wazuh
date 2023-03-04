--Deploy Ubuntu VM

sudo apt update

sudo apt install docker.io

sudo systemctl enable docker

sudo systemctl start docker

sudo apt install docker-compose

sudo git clone https://github.com/wazuh/wazuh-docker.git -b v4.3.10

cd single-node

docker-compose -f generate-indexer-certs.yml run --rm generator

echo 'vm.max_map_count=262144' | sudo tee -a /etc/sysctl.conf

sudo docker-compose up -d
