---
title: "Serving Assets to My Website"
date: 2020-05-03T23:05:19-07:00
draft: true
---

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
