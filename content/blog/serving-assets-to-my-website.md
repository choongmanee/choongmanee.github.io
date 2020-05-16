---
title: "Serving Assets to My Website"
date: 2020-05-09T17:48:30-07:00
draft: false
tags: 
- aws
- s3
- route53
- cloudfront
- certificate manager
- cdn
---

Serving assets, such as images and documents, to be accessible to end users is essential to a modern web experience. 
As for what I have in mind with this blog, I want to visually capture steps that I took to help jog my memory of
 what I did or learned. 
 
Setting this up took me 30 minutes the first time. The steps are split into a series of posts to keep the posts short
 and organized.
 
## Considerations
The fact that you're reading this post is a good indicator that this page loaded in a reasonable amount of time. 
{{<a href="https://www.fastcompany.com/1825005/how-one-second-could-cost-amazon-16-billion-sales" title="Fast Company">}}
reported that load times can be a critical factor to Amazon's sales and Google's search results. With that to
 keep in mind, here is my wishlist.

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

In a nutshell, I'm looking to have a content delivery network(CDN) with an outstanding storage offering.

## Using AWS to configure my CDN

The table below lists what I did with which service:  
*Some familiarity with AWS and the AWS Console is assumed*

| Action                                           | Route 53 | Certificate Manager | S3  | Cloudfront |
|--------------------------------------------------|:--------:|:-------------------:|:---:|:----------:|
| Have my domain in Route 53                       | x        |                     |     |            |
| Get a secure certificate for HTTPS               | o        | x                   |     |            |
| Create a S3 bucket                               |          |                     | x   |            |
| Create a Cloudfront distribution of my S3 bucket |          |                     | o   | x          |
| Add a new record for my Cloudfront distribution  | x        |                     |     | o          |

x: Primary AWS service; o: Related AWS service

### Have my domain in Route 53
1. From AWS Console, navigate to Route 53
    {{<img src="aws-route53-search.png" alt="search query for Route 53">}}
2. Go to **Domains** in the left panel and confirm `youdomain.com` is listed
    {{<img src="aws-route53-domain-listing.png" alt="list of domains in route 53">}}
    - If you don't have a registered domain, purchase a domain by clicking the **Register Domain** button

### Get a secure certificate for HTTPS
1. Click on **Services** in the header drop and type **Certificate Manager** in the search, follow the top suggestion
1. If you don't have any provisioned certificates, click **Get Started** under **Provision Certificates**.
    - If you have provisioned certificates but don't see any listed, navigate to the region where your provisioned
     certificates are listed.
1. Start a request for a certificate by clicking on the **Request a certificate** button
    {{<img src="aws-certificate-manager-request-certificate-buttons.png" alt="request a certificate button in AWS Certificate Manager">}}
    
    [!] Note the region you are working from provided in the header. Certificates are in the region from which
     they were initially requested.
    {{<img src="aws-certificate-manager-nav.png" alt="region in AWS header">}}
1. Select **Request a public certificate** and click **Request a certificate**
1. Complete the request process
    1. _Add domain names_:
        1. Enter `yourdomain.com` and click **Add another name to this certificate**
        1. Enter `*.yourdomain.com` and click **Next**
        {{<img src="aws-certificate-manager-flow1.png" alt="add domain names">}}
    1. _Select validation method_:
        1. Select **DNS validation** and click **Next**
    1. _Add Tags_:
        1. Enter as many tags as you'd like or none. Tags are similar to labels on AWS resources, can be used to
         communicate
         to other users about this resource, and a means for tracking costs.
    1. _Review_:
        1. Review for the following
            1. **Domain name**: `yourdomain.com`
            1. **Additional name**: `*.yourdomain.com`
            1. **Validation method**: `DNS`
        1. Click **Confirm and request** if everything looks right
    1. _Validation_:
        1. This process may take a few hours but generally completes in 15 minutes. While it validates, expand each
         row under **Domain** and perform the following:
            1. Click the blue **Create record in Route 53** button
            {{<img src="aws-certificate-manager-flow5.png" alt="validation">}}
            1. In the pop-up modal, click **Create**
        1. Click **Continue**
1. Verify the request in the table for `yourDomain.com` and it's status is either **Issued** or **Pending**
    {{<img src="aws-certificate-manager-complete-request.png" alt="complete request">}}

### Create a S3 bucket

1. Click on **Services** in the header drop and type **S3** in the search, follow the top suggestion
1. Click on **Create bucket** to start a bucket creation process
1. Under **General configuration**:
    1. Enter a *unique* bucket name
    1. Choose a region. General good practice is to select a region that is closest in proximity but also consider
     the availability zones in the region.
1. Under **Bucket settings for Block Public Access**
    1. Keep **Block all public access** checked. This protects your S3 bucket from being exposed to requests to the
     public. In the next section, we'll conigure Cloudfront to have access to your S3 and be responsible for
      distributing your assets.
1. Click on **Create bucket**

### Create a Cloudfront distribution for a S3 bucket
--- work in progress
### Add a new record in Route 53 for you Cloudfront distribution
--- work in progress
    
If you like this post, please feel free to support me.