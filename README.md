Since all your subdomains (including the newly added wa.aadikarta.org) are using a single certificate stored at /etc/letsencrypt/live/aadikarta.org/, you will need to expand your existing certificate to include the new subdomain.

docker compose exec certbot certbot certonly --webroot -w /var/www/certbot \
  --cert-name aadikarta.org \
  -d aadikarta.org \
  -d www.aadikarta.org \
  -d dev.aadikarta.org \
  -d api.aadikarta.org \
  -d admin.aadikarta.org \
  -d n8n.aadikarta.org \
  -d dev-meet.aadikarta.org \
  -d wa.aadikarta.org \
  -d itgoachq.org \
  -d www.itgoachq.org \
  -d api.itgoachq.org \
  --expand

After the certificate is successfully generated/expanded
docker compose exec nginx nginx -s reload
