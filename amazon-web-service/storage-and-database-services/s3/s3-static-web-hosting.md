# S3 Static Web Hosting

* S3 provides an option for a low-cost, highly-reliable hosting service for static websites 
* Static sites typically include HTML, CSS, and JavaScript files as well as images and fonts 
* When creating your static site you can specify an index file and an error file: 
  * The index file is the default file for your domain, for example, index.html 
  * The error file is used when there are 4xx errors for your site 
* Static web hosting will provide you with a unique URL endpoint for your website, the format for the URL depends on the region and is: bucket-name.s3-website\(- or .\)region.amazonaws.com 
* The URL for a static site in us-east-1 using a bucket called my-cool-site would be: my-cool-site.s3-website-us-east-1.amazonaws.com 
* Amazon Route 53 can also map human-readable domain names to static web hosting buckets, which are ideal for DNS failover solutions

## Cross-Origin Resource Sharing \(CORS\):

* CORS is a method of allowing a web application located in one domain to access and use resources in another domain 
* For AWS, this commonly means that a web application hosted in one S3 bucket can access resources in another S3 bucket 
* CORS settings can be configured inside of S3 on each bucket

