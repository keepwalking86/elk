# ELK Stack - docker-compose

## 1. Environment Variables

Edit .env with your cluster information (version, username, password)

ELK_VERSION=7.17.9

ELASTIC_USERNAME=elastic
ELASTIC_PASSWORD=changeme

## 2. Run

`docker-compose up -d`

## 3. Check running processes

```
$> docker ps

CONTAINER ID   IMAGE                                    COMMAND                  CREATED          STATUS         PORTS                                                                                  NAMES
6772abc2b741   elk-stack-docker-compose-filebeat        "/usr/bin/tini -- /u…"   2 minutes ago    Up 2 minutes                                                                                          elk-stack-docker-compose-filebeat-1
428477a41f8a   elk-stack-docker-compose-logstash        "/usr/local/bin/dock…"   53 minutes ago   Up 2 minutes   0.0.0.0:5044->5044/tcp, :::5044->5044/tcp, 0.0.0.0:9600->9600/tcp, :::9600->9600/tcp   elk-stack-docker-compose-logstash-1
92a2aa91502c   elk-stack-docker-compose-kibana          "/bin/tini -- /usr/l…"   2 hours ago      Up 2 minutes   0.0.0.0:5601->5601/tcp, :::5601->5601/tcp                                              elk-stack-docker-compose-kibana-1
829a2b87f487   elk-stack-docker-compose-elasticsearch   "/bin/tini -- /usr/l…"   2 hours ago      Up 2 minutes   0.0.0.0:9200->9200/tcp, :::9200->9200/tcp, 0.0.0.0:9300->9300/tcp, :::9300->9300/tcp   elk-stack-docker-compose-elasticsearch-1

```

## 4. Check Elasticsearch

Check indexes

`curl http://localhost:9200/_cat/indices?v -u elastic:changeme`

```
health status index                             uuid                   pri rep docs.count docs.deleted store.size pri.store.size
green  open   .security-7                       VfaWia0hReaeT4gHLLk98w   1   0         53            0    272.7kb        272.7kb
green  open   .apm-custom-link                  nv8eIoW_TlOeIx_4Yjj4ZQ   1   0          0            0       226b           226b
green  open   .kibana_7.17.9_001                jdepfQHsTGCKwLwDydml0g   1   0         26           10      4.7mb          4.7mb
green  open   .kibana_task_manager_7.17.9_001   iW8VDh2ATE22Bgeh8YyqgA   1   0         18          303    169.4kb        169.4kb
green  open   .apm-agent-configuration          7wwtA419Q6WEqDPGrjCzAg   1   0          0            0       226b           226b
green  open   .monitoring-logstash-7-2023.03.26 zOk0CcPCQQWju84TxoiGnQ   1   0       1890            0    827.7kb        827.7kb
green  open   .monitoring-kibana-7-2023.03.26   amHVCjieS9GKyIm7fVCkSw   1   0        882            0    511.4kb        511.4kb
yellow open   syslog-2023-03-26                 CEAfTUQWSy6xtA8Kr-DvTg   1   1      94409            0     29.5mb         29.5mb
green  open   .tasks                            Mc3yrJHfQbWUUzLsXkpa4A   1   0         11            3     77.7kb         77.7kb
green  open   .monitoring-es-7-2023.03.26       xnDGXIk3RfiEI8RFVZ45kA   1   0       6383          221      3.9mb          3.9mb
```

## 5. Access to Kibana

`http://localhost:5601`

Enter user/passsword: elastic/changeme
