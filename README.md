# CoreDNS

---

## DNS Primer

If you already know DNS, feel free to go grab a cup of coffee for a few minutes.

---

## Tooling

```bash
dig rocdev.org

; <<>> DiG 9.10.6 <<>> rocdev.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 46547
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;rocdev.org.                    IN      A

;; ANSWER SECTION:
rocdev.org.             299     IN      A       104.236.88.86

;; Query time: 52 msec
;; SERVER: 192.168.86.1#53(192.168.86.1)
;; WHEN: Tue Apr 07 20:33:19 EDT 2020
;; MSG SIZE  rcvd: 55
```

---

## Records

1. A
1. AAAA
1. CNAME
1. MX
1. TXT
1. SRV

---

### A Record

rocdev.org -> 104.236.88.86

google.com -> 172.217.4.78

---

### AAAA Record

IPv6 version of an A record.

google.com -> 2607:f8b0:4009:802::200e

---

### AAAA Record

```bash
dig google.com AAAA

; <<>> DiG 9.10.6 <<>> google.com AAAA
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 50227
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;google.com.                    IN      AAAA

;; ANSWER SECTION:
google.com.             299     IN      AAAA    2607:f8b0:4009:802::200e

;; Query time: 52 msec
;; SERVER: 192.168.86.1#53(192.168.86.1)
;; WHEN: Tue Apr 07 20:31:58 EDT 2020
;; MSG SIZE  rcvd: 67
```

---

### CNAME Record

bounces.rocdev.org -> sparkpostmail.com

```bash
dig bounces.rocdev.org

; <<>> DiG 9.10.6 <<>> bounces.rocdev.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 26406
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;bounces.rocdev.org.            IN      A

;; ANSWER SECTION:
bounces.rocdev.org.     299     IN      CNAME   sparkpostmail.com.

;; AUTHORITY SECTION:
sparkpostmail.com.      534     IN      SOA     ns-1855.awsdns-39.co.uk. awsdns-hostmaster.amazon.com. 1 7200 900 1209600 86400

;; Query time: 84 msec
;; SERVER: 192.168.86.1#53(192.168.86.1)
;; WHEN: Tue Apr 07 20:45:08 EDT 2020
;; MSG SIZE  rcvd: 162
```

---

### MX Record

rocdev.org -> in1-smtp.messagingengine.com

---

### TXT Record

It's a key-value store!

rocdev.org -> v=spf1 include:spf.messagingengine.com ?all
rocdev.org -> google-site-verification=POI99v6H4Btfzne5SErHxX1RpMTHw6oMgFIR_UAT3L4

---

### SRV Record

Microservices <3

```
_service._proto.name. TTL class SRV priority weight port target.
```

```
_sip._tcp.example.com. 86400 IN SRV 0 5 5060 sipserver.example.com.
```

---

## Authoritative Responses

```bash
dig rocdev.org SOA

; <<>> DiG 9.10.6 <<>> rocdev.org SOA
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 65220
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;rocdev.org.                    IN      SOA

;; ANSWER SECTION:
rocdev.org.             3599    IN      SOA     jim.ns.cloudflare.com. dns.cloudflare.com. 2033505715 10000 2400 604800 3600

;; Query time: 59 msec
;; SERVER: 192.168.86.1#53(192.168.86.1)
;; WHEN: Fri Apr 10 18:38:21 EDT 2020
;; MSG SIZE  rcvd: 100
```

---

## Zones

A domain for which your server claims to know a thing or two.

---

## Live Coding CoreDNS!

Skip Ahead: [https://github.com/geowa4/learn-coredns](https://github.com/geowa4/learn-coredns)

