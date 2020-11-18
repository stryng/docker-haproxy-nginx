# docker-haproxy-nginx

## Usage

```bash
~/repos/docker-haproxy-nginx ● docker-compose up -d
Creating network "docker-haproxy-nginx_default" with the default driver
Creating docker-haproxy-nginx_nginx2_1  ... done
Creating docker-haproxy-nginx_nginx4_1  ... done
Creating docker-haproxy-nginx_haproxy_1 ... done
Creating docker-haproxy-nginx_nginx3_1  ... done
Creating docker-haproxy-nginx_nginx1_1  ... done
Creating docker-haproxy-nginx_nginx5_1  ... done
 ~/repos/docker-haproxy-nginx ● docker ps -a
 
CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS              PORTS                                          NAMES
ece9785b8f8f        docker-haproxy-nginx_nginx1    "/docker-entrypoint.…"   5 seconds ago       Up 3 seconds        80/tcp                                         docker-haproxy-nginx_nginx1_1
41873b71b808        docker-haproxy-nginx_nginx5    "/docker-entrypoint.…"   5 seconds ago       Up 3 seconds        80/tcp                                         docker-haproxy-nginx_nginx5_1
471cd1d5800e        docker-haproxy-nginx_nginx3    "/docker-entrypoint.…"   5 seconds ago       Up 3 seconds        80/tcp                                         docker-haproxy-nginx_nginx3_1
87ae03a4c69c        docker-haproxy-nginx_nginx2    "/docker-entrypoint.…"   5 seconds ago       Up 4 seconds        80/tcp                                         docker-haproxy-nginx_nginx2_1
2e1c58db3ec0        docker-haproxy-nginx_haproxy   "/docker-entrypoint.…"   5 seconds ago       Up 4 seconds        0.0.0.0:8404->8404/tcp, 0.0.0.0:80->8080/tcp   docker-haproxy-nginx_haproxy_1
98eb8647d8ba        docker-haproxy-nginx_nginx4    "/docker-entrypoint.…"   5 seconds ago       Up 3 seconds        80/tcp                                         docker-haproxy-nginx_nginx4_1
```
