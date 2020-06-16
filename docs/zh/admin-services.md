# 服务启停

使用由Websoft9提供的 Kibana 部署方案，可能需要用到的服务如下：

## Kibana

```shell
sudo systemctl start kibana-server
sudo systemctl stop kibana-server
sudo systemctl restart kibana-server
sudo systemctl status kibana-server

# you can use this debug mode if Kibana service can't run
kibana-server console
```

### MySQL

```shell
sudo systemctl start mysql
sudo systemctl stop mysql
sudo systemctl restart mysql
sudo systemctl status mysql
```

### Redis

```shell
systemctl start redis
systemctl stop redis
systemctl restart redis
systemctl status redis
```