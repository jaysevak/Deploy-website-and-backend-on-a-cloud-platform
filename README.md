# S3 Website Hosting with CloudFront

This repository contains a static website designed to be hosted on Amazon S3 and delivered through CloudFront for low latency.

## Deployment Steps

1. **Create an S3 bucket**
   - Sign in to the AWS Management Console
   - Navigate to S3 service
   - Create a new bucket with a unique name
   - Unblock all public access (for website hosting)

2. **Enable static website hosting**
   - Select your bucket and go to the "Properties" tab
   - Scroll down to "Static website hosting" and click "Edit"
   - Enable static website hosting
   - Set "index.html" as the index document
   - Save changes

3. **Set bucket permissions**
   - Go to the "Permissions" tab
   - Update the bucket policy to allow public read access:
   ```json
   {
       "Version": "2012-10-17",
       "Statement": [
           {
               "Sid": "PublicReadGetObject",
               "Effect": "Allow",
               "Principal": "*",
               "Action": "s3:GetObject",
               "Resource": "arn:aws:s3:::your-bucket-name/*"
           }
       ]
   }
   ```

4. **Upload website files**
   - Upload all HTML, CSS, JavaScript, and image files to the bucket
   - Ensure proper content types are set for each file

5. **Create CloudFront distribution**
   - Navigate to CloudFront service
   - Create a new distribution
   - Select your S3 bucket as the origin
   - Configure the following settings:
     - Origin domain: Your S3 website endpoint
     - Viewer protocol policy: Redirect HTTP to HTTPS
     - Cache policy: CachingOptimized
     - Price class: Choose based on your needs
   - Create the distribution

6. **Access your website**
   - Once the CloudFront distribution is deployed, access your website using the CloudFront domain name
   - Example: `https://d1234abcdef.cloudfront.net`

## Benefits of CloudFront

- **Low Latency**: Content is delivered from edge locations closest to users
- **High Availability**: Built on AWS's global infrastructure
- **Security**: HTTPS support and integration with AWS Shield for DDoS protection
- **Cost Effective**: Pay only for the data transferred and requests made

## Project Structure

- `index.html` - Main landing page
- `tutorials.html` - Tutorials page
- `projects.html` - Projects page
- `about.html` - About page
- `contact.html` - Contact page
- Additional pages for blog, FAQ, help center, etc.

## Technologies Used

- HTML5
- CSS3
- JavaScript
- Font Awesome for icons
- AWS S3 for hosting
- AWS CloudFront for content delivery