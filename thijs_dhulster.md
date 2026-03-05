# https://tdhulster.github.io/knowledge-graphs-ugent-2026/profile.ttl

## Lab 2 - Part 5

`curl -I https://tdhulster.github.io/knowledge-graphs-ugent-2026/profile.ttl\#me`

### Output 
```
HTTP/2 200
server: GitHub.com
content-type: text/turtle; charset=utf-8
last-modified: Wed, 04 Mar 2026 21:22:20 GMT
access-control-allow-origin: *
etag: "69a8a28c-3dd"
expires: Thu, 05 Mar 2026 22:46:44 GMT
cache-control: max-age=600
x-proxy-cache: MISS
x-github-request-id: E9B4:28EBB:D7CE76:D9BB1E:69AA057C
accept-ranges: bytes
age: 0
date: Thu, 05 Mar 2026 22:36:44 GMT
via: 1.1 varnish
x-served-by: cache-bru1480052-BRU
x-cache: MISS
x-cache-hits: 0
x-timer: S1772750204.393986,VS0,VE120
vary: Accept-Encoding
x-fastly-request-id: 4dbdb2dac2035a161b6ab1b886cc2743e65f550d
content-length: 989
```

### Comments 

- `Content-type` is `text/turtle; charset=utf-8` since Github Pages correctly detects the proper MIME type from the file extension (.ttl) and puts `text/turtle` in the `Content-type` header.

- `access-control-allow-origin: *` : Github returns `*` as CORS header which allows every origin to request the resources.

- `cache-control: max-age=600` : makes sure the resource is cached for 5 minutes before - looks like this is cached in a Varnish cache

- `expires` header is ignored due to the previous `cache-control: max-age` header

- `etag` header is present and can be used for optimal client caching by sending it in a `if-none-match` header in subsequent requests

- `vary: Accept-Encoding` header indicates that the caching takes into account the 'Accept-Encoding' header. 