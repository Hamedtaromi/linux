# Host 1


### 1-update & upgrade

sudo dnf update -y

### 2-essential items for installing kafka
sudo dnf install -y java-17-openjdk java-17-openjdk-devel



### 3-download & unzip
wget https://downloads.apache.org/kafka/3.6.0/kafka_2.13-3.6.0.tgz
tar -xzf kafka_2.13-3.6.0.tgz
sudo mv kafka_2.13-3.6.0 /opt/kafka

### 4-creat user & change owner

sudo useradd kafka -m
sudo chown -R kafka:kafka /opt/kafka

### 5-enable service

systemctl enable --now confluent-zookeeper.service

systemctl enable --now confluent-kafka.service

### 6-start service

systemctl start confluent-zookeeper.service

systemctl start confluent-kafka.service

### 7-craet topic
kafka-topics --bootstrap-server host 1:9092 --create --topic my-topic




### 8-config kafka & kafka cluster
vim /etc/kafka/server.properties

zookeeper.connect=host 1 ,host 2 :2181

advertised.listeners=PLAINTEXT://host 1 :9092

listeners=PLAINTEXT://host 1:9092

broker.id=0

### 10-check kafka & zookeeper
systemctl restart confluent-zookeeper.service
systemctl status confluent-zookeeper.service
systemctl restart confluent-kafka.service
systemctl status confluent-kafka.service

### 11-producer topic

kafka-console-prooducer --topic my-topic --bootstrap-server host 1 :9092
