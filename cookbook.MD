## DOCKER

docker kill $(docker ps -q)

docker stop  $(docker ps --all -q)
docker rm $(docker ps --all -q)
docker rmi  $(docker images --all -q)
docker volume rm $(docker volume ls -q)

docker system prune -a

## NGINX




## LINUX
adduser developer
sudo groupadd docker
usermod -aG sudo developer
su - developer
sudo usermod -aG docker $USER

SSL Steps
openssl genpkey -algorithm RSA -out server.key
openssl req -new -key server.key -out server.csr
openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt
openssl pkcs12 -export -out server.pfx -inkey server.key -in server.crt

sudo snap install --classic certbot
sudo ln -s /snap/bin/certbot /usr/bin/certbot

sudo docker run -it --rm --name certbot \
            -v "/etc/letsencrypt:/etc/letsencrypt" \
            -v "/var/lib/letsencrypt:/var/lib/letsencrypt" \
            certbot/certbot certonly -d baronitech.com.br

docker compose run --rm  certbot certonly --webroot --webroot-path /var/www/certbot/ --dry-run -d example.org
## WINDOWS