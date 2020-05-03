---
title: "Route53 With Github Pages"
date: 2020-05-02T22:12:41-07:00
draft: true
---

Prior to this post, my blog was on a subdomain <https://blog.chungman.kim> while my domain <https://chungman.kim> was a
 blank page. The reason for this forked approach was to try [Github Pages](https://pages.github.com/) and [AWS S3
 ][2] for static web hosting. While both are great
 , I've decided to streamline my build processes to one target url. Here's what I had to do:
 
### Troubleshooting
If you are getting an error about your certificate but have followed all the steps, try ___ with another web browser
. If ___ works in your other browser, you may need to restart the browser with the issue.

### Certifying my domain in AWS

### Updating Github Pages

### Configuring Route53 with Github Pages
link to https://github.community/t5/GitHub-Pages/GitHub-Pages-with-Route-53-DNS/td-p/37739#
 
### Redirecting blog.chungman.kim using AWS
Redirecting blog.chungman.kim was easy following this [guide.][3] 

I've illustrated my steps below:
1. Navigate to S3 and click `Create Bucket`
2. Enter the name of the url you want to redirect from
![form](/images/s3.console.aws.amazon.com_s3_bucket_create_region=us-west-2.png)
+ Select a region and leave `Block all public access` checked
3. Click `Create Bucket`
4. In your list of buckets, click on the bucket you just created
5. Go into `Properties` and click the **Static Website Hosting** tile
6. Select the `Redirect requests` radio button and enter your target url to redirect to and protocol
7. Navigate to Route53 and select the hosted zone for where you want to redirect from
8. Set the A record for the origin url to have the following

[1]: https://pages.github.com/
[2]: https://docs.aws.amazon.com/AmazonS3/latest/dev/WebsiteHosting.html
[3]: https://aws.amazon.com/premiumsupport/knowledge-center/redirect-domain-route-53/