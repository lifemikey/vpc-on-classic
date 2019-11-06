---
copyright:
  years: 2018-2019
lastupdated: "2019-06-11"

keywords: resource, storage, connection, COS, object, endpoints, cross-region, regional, datacenter, vpc

subcollection: vpc-on-classic

---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}
{:external: target="_blank" .external}

# Connecting to IBM Cloud Object Storage from VPC
{: #connecting-to-ibm-cloud-object-storage-from-a-vpc}

This document shows you how to connect to {{site.data.keyword.cloud}} Object Storage from your Virtual Private Cloud. The endpoint information applies specifically to {{site.data.keyword.cloud_notm}} Virtual Private Cloud in the Classic Infrastructure environment.
{: shortdesc}


## What is IBM Cloud Object Storage (COS)?
{: #what-is-ibm-cloud-object-storage-cos}

{{site.data.keyword.cloud}} Object Storage (COS) is a web-scale platform that stores unstructured data. It provides reliability, security, availability, and disaster recovery without replication.

Information stored with {{site.data.keyword.cloud_notm}} Object Storage is encrypted and dispersed across multiple geographic locations. It is accessible through an implementation of the S3 API. This service makes use of the distributed storage technologies provided by the IBM Cloud Object Storage System.

IBM Cloud Object Storage is available with three types of configurations for resiliency: **Cross Region**, **Regional**, and **Single Datacenter**.
* **Cross Region** service provides higher durability and availability than using a single region, at the cost of slightly higher latency. This service is available today in the U.S., E.U., and A.P. areas.
* **Regional** service reverses the tradeoffs. It distributes objects across multiple availability zones within a single region. It is available in the U.S., E.U. and A.P. regions. If a given region or zone is unavailable, the object store continues to function without impediment.
**Single Datacenter** service distributes objects across multiple machines within the same physical location. Check this document regularly for available regions.

### COS direct endpoints for use with VPC
{: #cos-direct-endpoints-for-use-with-vpc}

To send a REST API request, you must set a target endpoint or a URL, and each COS storage location must have its own set of URLs. Direct endpoints provide your servers with high-speed, direct connections to {{site.data.keyword.cloud_notm}} services, which incur no added bandwidth costs. With the COS direct endpoint, a VPC can connect to a COS bucket located anywhere in the world.

There is no charge for traffic from your VPCs to all COS endpoints listed on this page.
{: note}

* A VPC client also has access to the COS bucket over the public endpoint.
* A VPC client only has access to the [COS Configuration API](https://{DomainName}/apidocs/cos/cos-configuration){: external} over the public endpoint, not the direct endpoint. The COS Configuration API can be used to configure some COS features on buckets, as well as to view bucket metadata.
* A VPC client does not have access to a COS bucket when the firewall is enabled.

## How to connect to IBM Cloud Object Storage (COS) from a VPC
{: #how-to-connect-to-ibm-cloud-object-storage-cos-from-a-vpc}

1. Provision COS from the [catalog](https://{DomainName}/catalog/services/cloud-object-storage){: external}.
2. Create a COS bucket in one of the regions listed in the following section.
3. Use the endpoint to communicate with your COS bucket.

### Regional endpoints
{: #regional-endpoints}

Buckets created at a regional endpoint distribute data across three datacenters, which are spread across a metropolitan area. Any single one of these datacenters can suffer an outage, or even destruction, without affecting availability.

| **Region** | **Endpoint** |
|------------|-------------------------------|
| U.S. South | `s3.direct.us-south.cloud-object-storage.appdomain.cloud`|
| U.S. East | `s3.direct.us-east.cloud-object-storage.appdomain.cloud`|
| E.U. United Kingdom | `s3.direct.eu-gb.cloud-object-storage.appdomain.cloud`|
| E.U. Germany | `s3.direct.eu-de.cloud-object-storage.appdomain.cloud`|
| A.P. Australia | `s3.direct.au-syd.cloud-object-storage.appdomain.cloud`
| A.P. Japan | `s3.direct.jp-tok.cloud-object-storage.appdomain.cloud` |


### Cross-region endpoints
{: #cross-region-endpoints}

Buckets created at a cross-region endpoint distribute data across three regions. Any one of these regions can suffer an outage or even destruction without affecting availability. Requests are routed to the nearest region's datacenter using Border Gateway Protocol (BGP) routing.

In the case of an outage, requests are re-routed to an active region, automatically. Advanced users who wish to write their own failover logic may do so, by sending requests to the specific region's endpoint and bypassing the BGP routing.

| **U.S. Cross Region** | **Endpoint** |
|------------|-------------------------------|
| U.S. Cross Region | `s3.direct.us.cloud-object-storage.appdomain.cloud` |
| Dallas Access Point | `s3.direct.dal.us.cloud-object-storage.appdomain.cloud` |
| San Jose Access Point | `s3.direct.sjc.us.cloud-object-storage.appdomain.cloud` |

| **E.U. Cross Region** | **Endpoint** |
|------------|-------------------------------|
| E.U. Cross Region | `s3.direct.eu.cloud-object-storage.appdomain.cloud` |
| Amsterdam Access Point | `s3.direct.ams.eu.cloud-object-storage.appdomain.cloud` |
| Frankfurt Access Point | `s3.direct.fra.eu.cloud-object-storage.appdomain.cloud` |
| Milan Access Point | `s3.direct.mil.eu.cloud-object-storage.appdomain.cloud` |

| **Asia Pacific Cross Region** | **Endpoint** |
|------------|-------------------------------|
| A.P. Cross Region | `s3.direct.ap.cloud-object-storage.appdomain.cloud` |
| Tokyo Access Point | `s3.direct.tok.ap.cloud-object-storage.appdomain.cloud` |
| Seoul Access Point | `s3.direct.seo.ap.cloud-object-storage.appdomain.cloud` |
| Hong Kong Access Point | `s3.direct.hkg.ap.cloud-object-storage.appdomain.cloud` |


 ### Single datacenter endpoints
 {: #single-datacenter-endpoints}

Single datacenters are not co-located with IBM Cloud services, such as IAM or Key Protect, and they offer no resiliency in the event of a site's outage or destruction.

If a networking failure results in a partition, such that the datacenter is unable to reach a core IBM Cloud region for access to IAM, authentication and authorization information is read from a cache that may become stale. This action may result in a lack of enforcement of new or altered IAM policies for up to 24 hours.
{:important}

| **Region** | **Endpoint** |
|------------|-------------------------------|
| Amsterdam, Netherlands | `s3.direct.ams03.cloud-object-storage.appdomain.cloud` |
| Chennai, India | `s3.direct.che01.cloud-object-storage.appdomain.cloud` |
| Hong Kong | `s3.direct.hkg02.cloud-object-storage.appdomain.cloud` |
| Melbourne, Australia | `s3.direct.mel01.cloud-object-storage.appdomain.cloud` |
| Mexico City, Mexico | `s3.direct.mex01.cloud-object-storage.appdomain.cloud` |
| Milan, Italy | `s3.direct.mil01.cloud-object-storage.appdomain.cloud` |
| Montréal, Canada | `s3.direct.mon01.cloud-object-storage.appdomain.cloud` |
| Oslo, Norway | `s3.direct.osl01.cloud-object-storage.appdomain.cloud` |
| Paris, France | `s3.direct.par01.cloud-object-storage.appdomain.cloud` |
| San Jose, USA | `s3.direct.sjc04.cloud-object-storage.appdomain.cloud` |
| São Paulo, Brazil | `s3.direct.sao01.cloud-object-storage.appdomain.cloud` |
| Seoul, South Korea | `s3.direct.seo01.cloud-object-storage.appdomain.cloud` |
| Toronto, Canada | `s3.direct.tor01.cloud-object-storage.appdomain.cloud` |
