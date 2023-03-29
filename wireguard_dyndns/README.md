Simple setup for wireguard and dyndns via cloudflare

Steps:

1. Set up docker swarm somewhere

Notes: https://docs.docker.com/engine/reference/commandline/swarm_init/

Usual command:
```
docker swarm init --advertise-addr 192.168.99.121
```

2. Configure dyndns.

2.1. If you have your own domain name in cloudflare:

- Get a cloudflare api token - https://dash.cloudflare.com/profile/api-tokens
- It needs: Zone:Read, DNS:Edit for your domain
- Fill in api token in configs/ddclient_ro.conf - password=fill_in_cloudflare_api_token

2.2. If not, use any other dyndns provider and update the file as needed.

3. Update Update example.com/subdomain.example.com to domain/subdomain you want to use in configs/ddclient_ro.conf and docker-compose.yml

3. start it up

```
./start.sh
```

4. To get a status if it doesn't start containers


```
docker stack ps --no-trunc main
```

5. Forward wireguard port (51820) and set up firewall as needed