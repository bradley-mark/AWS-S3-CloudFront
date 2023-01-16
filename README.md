# AWS-S3-CloudFront

Amazon S3 does not support HTTPS access to the website. If you want to use HTTPS, you can use Amazon CloudFront to serve a static website hosted on Amazon S3.

You can use Amazon CloudFront to improve the performance of your Amazon S3 website. CloudFront makes your website files (such as HTML, images, and video) available from data centers around the world (known as edge locations). When a visitor requests a file from your website, CloudFront automatically redirects the request to a copy of the file at the nearest edge location. This results in faster download times than if the visitor had requested the content from a data center that is located farther away.

CloudFront caches content at edge locations for a period of time that you specify. If a visitor requests content that has been cached for longer than the expiration date, CloudFront checks the origin server to see if a newer version of the content is available. If a newer version is available, CloudFront copies the new version to the edge location. Changes that you make to the original content are replicated to edge locations as visitors request the content.

**Simple overview** **S3+CloudFront**

![image](https://user-images.githubusercontent.com/91480603/211872481-23ed081b-d44d-4180-b964-1a15bad6dcd7.png)

# Create a CloudFront distribution

**To create a distribution with an Amazon S3 origin**

1. Open the CloudFront console at **https://console.aws.amazon.com/cloudfront/v3/home**
2. Choose **Create Distribution**
3. On the **Create Distribution** page, in the **Origin Settings** section, for **Origin Domain Name**, enter the Amazon S3 website endpoint for your bucket - **s3.markbradley.cloud.s3-website-us-east-1.amazonaws.com**
4. For **Default Cache Behavior** Settings, keep the values set to the defaults
5. For **Viewer** Settings, Viewer protocol policy default is **HTTP and HTTPS**, choose **HTTPS only**
6. For **Distribution Settings**, leave **Price Class** set to **Use all Edge Locations (Best Performance)**
7. Leave all other defaults and choose **Create distribution**
8. Record the value of **Domain Name** shown in the CloudFront > Distributions console - example: **https://d13gl6jkv1tr9.cloudfront.net**
9. Verify the CloudFront distribution is working by entering the domain name in a web browser

![image](https://user-images.githubusercontent.com/91480603/211874671-0a8b77c4-9d46-497c-8828-209465c67f5c.png)

# Edit CloudFront distribution with custom domain and SSL cert

**Simple overview** **S3+Route53+CloudFront+AWS Certificate Manager**

![image](https://user-images.githubusercontent.com/91480603/211873795-5b9d8b76-024d-405f-b497-61f210f499cd.png)

**AWS Certificate Manager (ACM)**

1. Choose **Request certificate**
2. Request a public certificate choose **Next**
3. Type **Fully qualified domain name**
4. Choose **Validation method** either *DNS validation** or **Email validation**
5. Choose **Key algorithm** default RSA 2048
6. Choose Request

