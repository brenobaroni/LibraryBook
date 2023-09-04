
    certbot:
      image: certbot/certbot:latest
      volumes:
        - ./certbot/www/:/var/www/certbot/:rw
        - ./certbot/conf/:/etc/letsencrypt/:rw


# Generate
    docker compose run --rm  certbot certonly --webroot     --webroot-path /var/www/certbot/ -d api.baronitech.com.br


# Renew All
    docker compose run --rm certbot renew
