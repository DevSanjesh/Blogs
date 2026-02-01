---
title: "DNS Record Types"
datePublished: Sat Jan 31 2026 07:51:15 GMT+0000 (Coordinated Universal Time)
cuid: cml20jdhm000d02l8306hgkzd
slug: dns-record-types
tags: chaicode, chaicode-webdev-cohort-2026

---

### Complete Guide to Understanding the Internet’s Invisible Infrastructure

---

## **About This Guide**

The Domain Name System (DNS) is the backbone of the internet, translating human-readable domain names into machine-readable IP addresses. Every time you visit a website, send an email, or connect to any online service, DNS makes it possible.

This comprehensive guide covers everything you need to know about DNS records—from the fundamentals of A and AAAA records to advanced security configurations with DNSSEC and CAA records. Whether you're a developer, system administrator, or simply curious about how the internet works, this guide will equip you with practical knowledge and best practices to enhance your understanding.

<table><tbody><tr><td colspan="1" rowspan="1"><p><strong>What You’ll Learn</strong></p></td></tr></tbody></table>

* DNS
    
* All major DNS record types
    

---

### **CONTENTS**

1. What is DNS?
    
2. DNS Record Types
    

## What is DNS?

**DNS** is like the **phonebook of the internet** 📖📞.

* Humans remember names like [`example.com`](http://example.com)
    
* Computers understand IP addresses like `142.250.183.206`
    

DNS translates **domain names → IP addresses**, so browsers know where to go.

⚙️ **How Does DNS Work?**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769802911266/fd878e33-1768-491c-9c54-d9d529ecc421.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769802991131/166c5c7f-3714-4e89-98ac-8c19d0f25e3b.png align="center")

---

## **DNS Record Types: The Complete Reference**

DNS records are instructions stored in authoritative DNS servers that provide critical information about a domain. Each record type serves a specific purpose in translating domain names into actionable data.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769804783374/a72315a6-b3a6-41b1-86f5-2a1584ffb1a9.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769804653991/3b7e4b12-b183-448d-a209-9d3ca05e9740.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769804935008/3b97e6c8-c47a-4ecf-8a95-7c5f6a5bbccc.png align="center")

### 🅰️ **A Record (Address Record)**

The most fundamental DNS record type, mapping a domain name directly to an IPv4 address. This record directs traffic to your web server by translating domain names into IP addresses that computers use to connect.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769805182304/24b253f2-1814-4bfb-808d-81e350623426.png align="center")

### 🅰️🅰️ **AAAA Record (Quad-A Record)**

The IPv6 equivalent of an A record, pointing domains to 128-bit IPv6 addresses. Ensures your website is accessible via IPv6, future-proofing your infrastructure as IPv4 addresses become scarce.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769805514723/5f4c8d70-8a28-48c8-af34-140a912ed1d0.png align="center")

### 🔁 **CNAME Record (Canonical Name)**

Creates an alias that points one domain name to another domain name rather than directly to an IP address. Simplifies DNS management by allowing multiple domain names to resolve to a single canonical name.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769805654682/50fd3d8e-5fa9-4a38-863c-f97210c8911d.png align="center")

### 📧 **MX Record (Mail Exchange)**

Specifies mail servers responsible for receiving email for a domain, with priority values determining delivery order. Lower priority numbers are tried first; higher values serve as backups.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769806453047/0775429e-fd55-46f7-8c28-4375339d290c.png align="center")

### 📝 **TXT Record (Text Record)**

Stores arbitrary text data in DNS, commonly used for domain verification and email security (SPF, DKIM, DMARC).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769806704628/28cae2ad-9dcc-42f4-93ea-cb402af13976.png align="center")

### 🌍 **NS Record (Name Server)**

Identifies the authoritative DNS servers for a domain, directing queries to the servers containing actual DNS records.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769806842798/4320da85-d980-4248-9200-78878ace1d2e.png align="center")

### **SOA Record (Start of Authority)**

Contains administrative information about the DNS zone, including the primary nameserver and timing parameters.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769807027271/a79d9011-9cf5-4ff0-97d6-4b62455dde38.png align="center")

### **PTR Record (Pointer Record)**

Provides reverse DNS lookup capability, mapping IP addresses back to domain names. Critical for email servers, as many mail servers verify reverse DNS to prevent spam.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769842893669/f3ea1595-4dc1-48d6-8d7a-c318e1baff2b.png align="center")

### **SRV Record (Service Record)**

Specifies the location of services, including hostname and port number for specific protocols. Essential for VoIP services, XMPP chat servers, and Microsoft Active Directory.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769843082988/be863c88-4182-466a-a225-c11c9159e79d.png align="center")

### Summary

This guide provides an in-depth understanding of the Domain Name System (DNS), the essential yet often unseen infrastructure of the internet that translates domain names into IP addresses. Covering foundational to advanced topics, it delves into various DNS record types, including A, AAAA, CNAME, MX, TXT, NS, SOA, PTR, and SRV records. The guide is ideal for developers, system administrators, and anyone interested in internet functionality, offering practical insights and best practices to deepen their DNS knowledge.