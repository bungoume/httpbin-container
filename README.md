# httpbin-container
[httpbin](https://httpbin.org/) in docker container.

This application outputs [ltsv-formatted](http://ltsv.org/) access log.


# Usage

```
$ sudo docker run -d -p 80:80 -v /tmp/log:/log bungoume/httpbin-container
7b807754cf10a9df3c18ca1482f2f8197870873a87b344249d7256b4588e3fe4

$ curl http://localhost/get
{
  "args": {},
  "headers": {
    "Accept": "*/*",
    "Content-Length": "",
    "Content-Type": "",
    "Host": "localhost",
    "User-Agent": "curl/7.29.0"
  },
  "origin": "172.17.42.1",
  "url": "http://localhost/get"
}

$ ls /tmp/log
nginx_access.log  nginx_error.log  uwsgi_access.log  uwsgi_error.log

$ tail /tmp/log/nginx_access.log
time:2016-08-24T05:19:33+00:00  timestamp:1472015973.559        remote_addr:172.17.42.1 x_forwarded_for:-       x_forwarded_proto:-     scheme:http     method:GET      user:-  host:localhost  path:/get       query:- req_body:-      req_bytes:76    connection:19236        connection_requests:1   referer:-       accept_language:-       user_agent:curl/7.29.0  hostname:3c739d98407e   status:200      req_cache_control:-     res_cache_control:-     res_bytes:452   res_body_bytes:232      res_content_encoding:-  res_content_type:application/json       taken_time:0.003        upstream_cache_status:- upstream_addr:127.0.0.1:8000    upstream_taken_time:0.003

$ tail /tmp/log/uwsgi_access.log
time:24/Aug/2016:05:19:33 +0000 timestamp_us:1472015973556686   remote_addr:172.17.42.1 x_forwarded_for:-       x_forwarded_proto:-     method:GET      status:200      user:-  host:localhost  path:/get       query:- referer:-       taken_time_us:2437      req_body_bytes:0        res_bytes:376   res_body_bytes:232      app_worker:1    accept_language:-       user_agent:curl/7.29.0
```
