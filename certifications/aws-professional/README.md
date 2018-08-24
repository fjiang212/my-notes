# Core knowledges
https://linuxacademy.com/cp/guides/download/refsheets/guides/refsheets/aws-csa-pro_1470165599.pdf

## AWS And General IT Knowledge

## Enterprise Account Management

# Required Services


# Related knowledges
## DNS
https://www.digitalocean.com/community/tutorials/an-introduction-to-dns-terminology-components-and-concepts


* A `name server` is a computer designated to translate domain names into IP addresses. 

> Name servers can be "authoritative", meaning that they give answers to queries about domains under their control. Otherwise, they may point to other servers, or serve cached copies of other name servers' data.

* A `zone file` is a simple text file that contains the mappings between domain names and IP addresses. 

> Zone files reside in name servers and generally define the resources available under a specific domain, or the place that one can go to get that information.

*  Within a zone file, `records` are kept. In its simplest form, a record is basically a single mapping between a resource and a name. These can map a domain name to an IP address, define the name servers for the domain, define the mail servers for the domain, etc.

* `CNAME` records define an alias for canonical name for your server (one defined by an A or AAAA record).

```
server1     IN  A       111.111.111.111
www         IN  CNAME   server1
```


* The difference between a host name and a subdomain is that a host defines a computer or resource, while a subdomain extends the parent domain. It is a method of subdividing the domain itself.

