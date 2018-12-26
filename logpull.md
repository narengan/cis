---
copyright:
  years: 2018
lastupdated: "2018-12-19"
---

# Enterprise Log share

# Log Pull

IBM customers can access the Log Pull service on Enterprise accounts. This service allows users to consume request logs over HTTP using a RESTful API.
This API provides a method for customers to access a domain’s request logs using an IAM token.

These logs contain data related to the connecting client, the request path through the network, and the response from the origin web server.


## Examples:
1. **Based on Ray Id**

Request

```
curl -X GET -H "X-Auth-Token: Token1234" https://api.cis.cloud.ibm.com/v1/logpull/<URL-encoded-CRN>/zones/<zone-id>/logs/rayids/<ray-id>
```

Response

 ```
    {
    "ClientIP": "68.278.11.89",
    "ClientRequestHost": "testing.logpull.com",
    "ClientRequestMethod": "GET",
    "ClientRequestURI": "/var/www",
    "EdgeEndTimestamp": 1545155129703000000,
    "EdgeResponseBytes": 1935,
    "EdgeResponseStatus": 403,
    "EdgeStartTimestamp": 1545155129696000000,
    "RayID": "48b371889c489b2c"
}
```

2. **Based on time duration**

Required Parameters: 

Start and End time in UTC ISO-8601 date representation with a time duration of a minute or an hour.

Request:
```
curl -X GET -H "X-Auth-Token: Token1234" https://api.cis.cloud.ibm.com/v1/logpull/<URL-encoded-CRN>/zones/<zone-id>/logs/received?start=2018-12-17T17:27:00Z&end=2018-12-17T17:28:00Z
```
Response:
```
{"ClientIP":"2620:1f7:8c5::1f:949e:c04d","ClientRequestHost":"test.logpull.load.com","ClientRequestMethod":"GET","ClientRequestURI":"/assets/bootstrap-collapse.js","EdgeEndTimestamp":1545067628046000000,"EdgeResponseBytes":2205,"EdgeResponseStatus":200,"EdgeStartTimestamp":1545067628044000000,"RayID":"48ab19434891c7a7"}
{"ClientIP":"2620:1f7:8c5::1f:949e:c04d","ClientRequestHost":"test.logpull.load.com","ClientRequestMethod":"GET","ClientRequestURI":"/assets/3d.gif","EdgeEndTimestamp":1545067627970000000,"EdgeResponseBytes":2538446,"EdgeResponseStatus":200,"EdgeStartTimestamp":1545067627951000000,"RayID":"48ab1942bf96c7a7"}
{"ClientIP":"2620:1f7:8c5::1f:949e:c04d","ClientRequestHost":"test.logpull.load.com","ClientRequestMethod":"GET","ClientRequestURI":"/assets/logo.gif","EdgeEndTimestamp":1545067628051000000,"EdgeResponseBytes":82257,"EdgeResponseStatus":200,"EdgeStartTimestamp":1545067628048000000,"RayID":"48ab194348a0c7a7"}
{"ClientIP":"2620:1f7:8c5::1f:949e:c04d","ClientRequestHost":"test.logpull.load.com","ClientRequestMethod":"GET","ClientRequestURI":"/assets/docs.css","EdgeEndTimestamp":1545067627952000000,"EdgeResponseBytes":540,"EdgeResponseStatus":200,"EdgeStartTimestamp":1545067627948000000,"RayID":"48ab1942af8ac7a7"}
{"ClientIP":"2620:1f7:8c5::1f:949e:c04d","ClientRequestHost":"test.logpull.load.com","ClientRequestMethod":"GET","ClientRequestURI":"/assets/bootstrap.css","EdgeEndTimestamp":1545067627952000000,"EdgeResponseBytes":17311,"EdgeResponseStatus":200,"EdgeStartTimestamp":1545067627948000000,"RayID":"48ab1942af85c7a7"}
{"ClientIP":"2620:1f7:8c5::1f:949e:c04d","ClientRequestHost":"test.logpull.load.com","ClientRequestMethod":"GET","ClientRequestURI":"/assets/jquery.js","EdgeEndTimestamp":1545067628045000000,"EdgeResponseBytes":33555,"EdgeResponseStatus":200,"EdgeStartTimestamp":1545067628042000000,"RayID":"48ab19434882c7a7"}
{"ClientIP":"2620:1f7:8c5::1f:949e:c04d","ClientRequestHost":"test.logpull.load.com","ClientRequestMethod":"GET","ClientRequestURI":"/assets/watson.gif","EdgeEndTimestamp":1545067628052000000,"EdgeResponseBytes":893230,"EdgeResponseStatus":200,"EdgeStartTimestamp":1545067628046000000,"RayID":"48ab194348a3c7a7"}
{"ClientIP":"2620:1f7:8c5::1f:949e:c04d","ClientRequestHost":"test.logpull.load.com","ClientRequestMethod":"GET","ClientRequestURI":"/assets/bootstrap-386.js","EdgeEndTimestamp":1545067628046000000,"EdgeResponseBytes":1663,"EdgeResponseStatus":200,"EdgeStartTimestamp":1545067628043000000,"RayID":"48ab19434884c7a7"}
{"ClientIP":"2620:1f7:8c5::1f:949e:c04d","ClientRequestHost":"test.logpull.load.com","ClientRequestMethod":"GET","ClientRequestURI":"/assets/Fixedsys500c.woff","EdgeEndTimestamp":1545067630272000000,"EdgeResponseBytes":14055,"EdgeResponseStatus":200,"EdgeStartTimestamp":1545067629064000000,"RayID":"48ab1949aca2c7a7"}
{"ClientIP":"2620:1f7:8c5::1f:949e:c04d","ClientRequestHost":"test.logpull.load.com","ClientRequestMethod":"GET","ClientRequestURI":"/assets/bios.gif","EdgeEndTimestamp":1545067628055000000,"EdgeResponseBytes":1121237,"EdgeResponseStatus":200,"EdgeStartTimestamp":1545067628046000000,"RayID":"48ab1943489ec7a7"}
{"ClientIP":"2620:1f7:8c5::1f:949e:c04d","ClientRequestHost":"test.logpull.load.com","ClientRequestMethod":"GET","ClientRequestURI":"/assets/bootstrap-modal.js","EdgeEndTimestamp":1545067628046000000,"EdgeResponseBytes":2569,"EdgeResponseStatus":200,"EdgeStartTimestamp":1545067628043000000,"RayID":"48ab1943488ac7a7"}
{"ClientIP":"2620:1f7:8c5::1f:949e:c04d","ClientRequestHost":"test.logpull.load.com","ClientRequestMethod":"GET","ClientRequestURI":"/assets/holder.js","EdgeEndTimestamp":1545067628053000000,"EdgeResponseBytes":4593,"EdgeResponseStatus":200,"EdgeStartTimestamp":1545067628046000000,"RayID":"48ab19434898c7a7"}
{"ClientIP":"2620:1f7:8c5::1f:949e:c04d","ClientRequestHost":"test.logpull.load.com","ClientRequestMethod":"GET","ClientRequestURI":"/assets/old_school.png","EdgeEndTimestamp":1545067627960000000,"EdgeResponseBytes":1466,"EdgeResponseStatus":200,"EdgeStartTimestamp":1545067627952000000,"RayID":"48ab1942bf92c7a7"}
{"ClientIP":"2620:1f7:8c5::1f:949e:c04d","ClientRequestHost":"test.logpull.load.com,"ClientRequestMethod":"GET","ClientRequestURI":"/assets/bootstrap-responsive.css","EdgeEndTimestamp":1545067627951000000,"EdgeResponseBytes":4797,"EdgeResponseStatus":200,"EdgeStartTimestamp":1545067627948000000,"RayID":"48ab1942af86c7a7"}
```

3. **Fields**

If "fields" are not specified in the request, a limited set of default fields will be returned. The full list of all available fields can be found here:

Request

```
curl -X GET -H "X-Auth-Token: Token1234" https://api.cis.cloud.ibm.com/v1/logpull/<URL-encoded-CRN>/zones/<zone-id>/logs/received/fields
```

Fields are passed to the request as a comma separated list. So, to have "ZoneID" and "RayID", use:

```
fields=ZoneId,RayID
```

Field list:

Currently available fields (as of Dec 2018):
```
"CacheCacheStatus": "string; unknown | miss | expired | updating | stale | hit | ignored | bypass | revalidated",
    "CacheResponseBytes": "int; number of bytes returned by the cache",
    "CacheResponseStatus": "int; HTTP status code returned by the cache to the edge: all requests (including non-cacheable ones) go through the cache: also see CacheStatus field",
    "CacheTieredFill": "bool; tiered Cache was used to serve this request",
    "ClientASN": "int; client AS number",
    "ClientCountry": "string; country of the client IP address",
    "ClientDeviceType": "string; client device type",
    "ClientIP": "string; IP address of the client",
    "ClientIPClass": "string; client IP class",
    "ClientRequestBytes": "int; number of bytes in the client request",
    "ClientRequestHost": "string; host requested by the client",
    "ClientRequestMethod": "string; HTTP method of client request",
    "ClientRequestPath": "string; URI path requested by the client",
    "ClientRequestProtocol": "string; HTTP protocol of client request",
    "ClientRequestReferer": "string; HTTP request referrer",
    "ClientRequestURI": "string; URI requested by the client",
    "ClientRequestUserAgent": "string; User agent reported by the client",
    "ClientSSLCipher": "string; Client SSL cipher",
    "ClientSSLProtocol": "string; Client SSL (TLS) protocol",
    "ClientSrcPort": "int; client source port",
    "EdgeColoID": "int; Cloudflare edge colo id",
    "EdgeEndTimestamp": "int or string; unix nanosecond timestamp the edge finished sending response to the client",
    "EdgePathingOp": "string; indicates what type of response was issued for this request (unknown = no specific action)",
    "EdgePathingSrc": "string; details how the request was classified based on security checks (unknown = no specific classification)",
    "EdgePathingStatus": "string; indicates what data was used to determine the handling of this request (unknown = no data)",
    "EdgeRateLimitAction": "string; the action taken by the blocking rule; empty if no action taken",
    "EdgeRateLimitID": "int; the internal rule ID of the rate-limiting rule that triggered a block (ban) or simulate action. 0 if no action taken",
    "EdgeRequestHost": "string; host header on the request from the edge to the origin",
    "EdgeResponseBytes": "int; number of bytes returned by the edge to the client",
    "EdgeResponseCompressionRatio": "float; edge response compression ratio",
    "EdgeResponseContentType": "string; Edge response Content-Type header value",
    "EdgeResponseStatus": "int; HTTP status code returned by Cloudflare to the client",
    "EdgeServerIP": "string; IP of the edge server making a request to the origin",
    "EdgeStartTimestamp": "int or string; unix nanosecond timestamp the edge received request from the client",
    "OriginIP": "string; IP of the origin server",
    "OriginResponseBytes": "int; number of bytes returned by the origin server",
    "OriginResponseHTTPExpires": "string; value of the origin 'expires' header in RFC1123 format",
    "OriginResponseHTTPLastModified": "string; value of the origin 'last-modified' header in RFC1123 format",
    "OriginResponseStatus": "int; status returned by the origin server",
    "OriginResponseTime": "int; number of nanoseconds it took the origin to return the response to edge",
    "OriginSSLProtocol": "string; SSL (TLS) protocol used to connect to the origin",
    "ParentRayID": "string; ray id of the parent request if this request was made through a worker script",
    "RayID": "string; Ray ID of the request",
    "SecurityLevel": "string; the security level configured at the time of this request. This is used to determine the sensitivity of the IP Reputation system.",
    "WAFAction": "string; action taken by the WAF, if triggered",
    "WAFFlags": "string; additional configuration flags: simulate (0x1) | null",
    "WAFMatchedVar": "string; the full name of the most-recently matched variable",
    "WAFProfile": "string; WAF profile: low | med | high",
    "WAFRuleID": "string; ID of the applied WAF rule",
    "WAFRuleMessage": "string; rule message associated with the triggered rule",
    "WorkerCPUTime": "int; amount of time in microseconds spent executing a worker if any",
    "WorkerStatus": "string; status returned from worker daemon",
    "WorkerSubrequest": "bool; whether or not this request was a worker subrequest",
    "WorkerSubrequestCount": "int; number of subrequests issued by a worker when handling this request",
    "ZoneID": "int; internal zone ID"
```
