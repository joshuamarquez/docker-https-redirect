# docker-https-redirect

[![](https://images.microbadger.com/badges/version/joshuamarquez/https-redirect:0.1.0.svg)](https://microbadger.com/images/joshuamarquez/https-redirect:0.1.0 "Get your own version badge on microbadger.com") [![](https://images.microbadger.com/badges/image/joshuamarquez/https-redirect:0.1.0.svg)](https://microbadger.com/images/joshuamarquez/https-redirect:0.1.0 "Get your own image badge on microbadger.com")

NGINX docker image to redirect request from HTTP to HTTPS.

## Install

```sh
$ docker pull joshuamarquez/https-redirect
```

## Test

To test it actually works first run `https-redirect` instance.

```sh
$ docker run --name nginx_redirect -d https-redirect:latest
```

Then using `appropriate/curl` make a request.

```sh
$ docker run --network container:nginx_redirect appropriate/curl -Is $(docker ps -aqf "name=nginx_redirect")
```

It should respond with something like:

```
HTTP/1.1 301 Moved Permanently
Server: nginx/1.11.13
Date: Wed, 17 May 2017 00:35:51 GMT
Content-Type: text/html
Content-Length: 186
Connection: keep-alive
Location: https://7f708982c19d/
```