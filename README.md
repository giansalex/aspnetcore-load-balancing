# ASP.NET Core HTTPS & Load balancing
Deploy an ASP.NET Core application with HTTPS & Load balancing using Docker.


## Nginx
Using nginx as reverse proxy.

![docker-nginx](https://raw.githubusercontent.com/giansalex/aspnetcore-load-balancing/master/doc/target-architecture-docker-nginx-ketrel.png "ASP.NET CORE NGINX")

To get started:

```sh
git clone https://github.com/giansalex/aspnetcore-load-balancing.git
cd aspnetcore-load-balancing
docker-compose build
docker-compose up -d --scale core-app=4 --no-recreate
```

> IMPORTANT: Due to NGINX (Free version) limiations, current configuration is set to work with a fixed scale of 4 nodes.
With NGINX Plus, additional changes might be applied to scale up and down dynamically.

## Traefik
Using [Traefik](https://traefik.io/) Edge Router.

```bash
git clone https://github.com/giansalex/aspnetcore-load-balancing.git
cd aspnetcore-load-balancing
docker-compose -f docker-compose.traefik.yml build
docker-compose -f docker-compose.traefik.yml up -d --scale app=4
```

Navigate to https://localhost

![app-on-browser](https://raw.githubusercontent.com/giansalex/aspnetcore-load-balancing/master/doc/dotnetapp-on-browser.gif)