---
title: "Serving Assets to My Website"
date: 2020-05-03T23:05:19-07:00
draft: true
---

Serving assets, such as images and documents, to be accessible to end users is essential to a modern web experience. 
As for what I have in mind with this blog, I want to visually capture steps that I took to help jog my memory of
 what I did or learned. Evidently, here is an explanation of how I am hosting and serving my assets.
 
## Considerations
The fact that you're reading this post is a good indicator that this page loaded in a reasonable amount of time. 
[Fast Company][1] wrote an interesting article on how load times can be a critical factor to Amazon's sales and
 Google's search results. With that to keep in mind, here is my wishlist.

1. Low cost storage
1. Expandable storage
1. Storage durability (Would my assets remain in a natural disaster? Does the hosting company have foreseeable
 longevity?)
1. Secure storage management
1. Easy health checks
1. Controlled access to assets
1. Flawless or near flawless uptime
1. Low cost delivery
1. Fast content delivery
1. Configurable with my domain

In a nutshell, I'm looking to have a Content Delivery Network with an outstanding storage offering.

## Using AWS

As of this post, I have two AWS Certifications, Cloud Practitioner and Developer Associate, and a two years of hands-on
 AWS experience.
 
The table below lists what I did with which service in chronological order:
(This table assumes [IAM][iam] and that your domain is in AWS. If you )

| #     | Action | Route 53 | Certificate Manager | S3  | Cloudfront |
| :---: | ------ | :---: | :---: | :---: | :---: |
| 1     | Get a secure certificate |  | X |||



### Securing traffic with [Certificate Manager][2]

From the Certificate Manager website:
> AWS Certificate Manager is a service that lets you easily provision, manage, and deploy public and private Secure
> Sockets Layer/Transport Layer Security (SSL/TLS) certificates for use with AWS services and your internal connected
> resources. SSL/TLS certificates are used to secure network communications and establish the identity of websites
> over the Internet as well as resources on private networks. AWS Certificate Manager removes the time-consuming
> manual process of purchasing, uploading, and renewing SSL/TLS certificates.

1. 
read this first
https://aws.amazon.com/blogs/networking-and-content-delivery/amazon-s3-amazon-cloudfront-a-match-made-in-the-cloud/
understand this next
https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-restricting-access-to-s3.html

brainstorm
create cdn for fast delivery
store files with high durability
keep costs low with low cost storage and even lower cost retrieval
limit access to s3 bucket to only cf
provide an alias for cf endpoint

steps:
get a certificate
create a subdomain with route 53
create bucket in s3
create cloudfront distribution
add a file
test

{{<img src="hero.jpg" alt="sample">}}

[1]: https://www.fastcompany.com/1825005/how-one-second-could-cost-amazon-16-billion-sales
[iam]: https://aws.amazon.com/iam/
[2]: https://aws.amazon.com/certificate-manager/