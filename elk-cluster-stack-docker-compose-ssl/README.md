https://levelup.gitconnected.com/elasticsearch-kibana-security-authentication-and-network-encryption-enabled-with-docker-e6747a989766

# ELK cluster with TLS/SSL encryption - docker-compose

## 1. Environment Variables

Edit .env with your cluster information (version, username, password)

ELK_VERSION=7.17.9

ELASTIC_USERNAME=elastic
ELASTIC_PASSWORD=changeme

## 2. Run

`docker-compose up -d`

## 3. Access to Kibana

`http://localhost:5601`

Enter user/passsword: elastic/changeme