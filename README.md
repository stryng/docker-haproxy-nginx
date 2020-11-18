## Docker with HAProxy and x5 NginX webserver containers to distribute the load equaly - Horizontal Scaling

### Usage

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

### HAproxy Stats
![GitHub Logo](Screenshot%202020-11-18%20at%2013.47.02.png)

### LoadTesting --> HAProxy LoadBalancer @tcp:80 --> targeting containers @tcp:80
```
~  ab -n 10000 -c 30 http://localhost/index.html
This is ApacheBench, Version 2.3 <$Revision: 1879490 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking localhost (be patient)
Completed 1000 requests
Completed 2000 requests
Completed 3000 requests
Completed 4000 requests
Completed 5000 requests
Completed 6000 requests
Completed 7000 requests
Completed 8000 requests
Completed 9000 requests
Completed 10000 requests
Finished 10000 requests


Server Software:        nginx/1.18.0
Server Hostname:        localhost
Server Port:            80

Document Path:          /index.html
Document Length:        12 bytes

Concurrency Level:      30
Time taken for tests:   9.088 seconds
Complete requests:      10000
Failed requests:        0
Total transferred:      2420000 bytes
HTML transferred:       120000 bytes
Requests per second:    1100.32 [#/sec] (mean)
Time per request:       27.265 [ms] (mean)
Time per request:       0.909 [ms] (mean, across all concurrent requests)
Transfer rate:          260.04 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        0    1  20.4      0    1191
Processing:     5   26  10.9     25     104
Waiting:        4   26  10.7     24     104
Total:          5   27  23.0     25    1211

Percentage of the requests served within a certain time (ms)
  50%     25
  66%     29
  75%     33
  80%     35
  90%     41
  95%     47
  98%     55
  99%     60
 100%   1211 (longest request)
 ```
