# Install software
```bash
git clone https://github.com/sonnyyu/docker-portainer-stack
cd docker-portainer-stack
```
# Getting started portainer with certificate
```bash
docker-compose up -d
```
# Quit 
```bash
docker-compose down 
```
# Quit and remove Volume
```bash
docker-compose down -v
```
# Open Portainer from Browser
```bash
https://192.168.1.204:9443
```
### Install Server Certificate
# Use mtls-cert-manage generate server/client/ca certificate 

[https://github.com/sonnyyu/mtls-cert-manage](https://github.com/sonnyyu/mtls-cert-manage)

# Copy Certificate from mtls-cert-manage
```bash
cd ~/mtls-cert-manage/cert 
cp * ~/docker-portainer-stack/certs
```
# Make PEM for portainer
```bash
cd ~/docker-portainer-stack/certs
openssl x509 -inform PEM -in localhost.crt > localhost.pem
```
# Getting started portainer with certificate
```bash
docker-compose -f docker-compose-tls.yml up -d
```
# Quit 
```bash
docker-compose -f docker-compose-tls.yml down 
```
# Quit and remove Volume
```bash
docker-compose -f docker-compose-tls.yml down -v
```
# Import CA Certificate into PC
[Install certificate](https://github.com/sonnyyu/mtls-cert-manage#install-certificate-at-windows)

# Open Portainer from Browser
```bash
https://192.168.1.204:9443
```
# Reset Admin Password
```bash
docker stop portainer
docker run --rm -v portainer_data:/data portainer/helper-reset-password
docker start portainer
```
