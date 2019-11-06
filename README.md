# K8s homework 101
> so ..

### chart1
> 题目一
在chart1所在目录，执行一下命令

```sh
# dev环境
helm install -f values-hasher.yaml --name hasher-dev --namespace dev .
helm install -f values-worker.yaml --name worker-dev --namespace dev .
helm install -f values-rng.yaml --name rng-dev --namespace dev .
helm install -f values-webui.yaml --name webui-dev --namespace dev .
helm install -f values-redis.yaml --name redis-dev --namespace dev .

# uat环境
helm install -f values-hasher.yaml --name hasher-uat --namespace uat .
helm install -f values-worker.yaml --name worker-uat --namespace uat .
helm install -f values-rng.yaml --name rng-uat --namespace uat .
helm install -f values-webui.yaml --name webui-uat --namespace uat --set ingress.hosts[0].host=uat-webui.192.168.33.111.nip.io .
helm install -f values-redis.yaml --name redis-uat --namespace uat .

```

### chart2
> 题目二

虚拟机安装redis-server
```sh
sudo apt install redis-server -y
sudo sed -i "s/127.0.0.1/192.168.33.101/g" /etc/redis/redis.conf
sudo service redis-server restart
```

在chart2所在目录，执行一下命令
```sh
# prod环境
helm install --name webui --namespace prod .
```
