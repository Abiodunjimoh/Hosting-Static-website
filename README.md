# Hosting Static website with AWS S3 bucket
1.**Upload Your Website Files**
- Go to the S3 Console
- Select the bucket: mystaticwerj25
- Click Upload
- Add your website files (e.g. index.html, style.css, etc.)
- Make sure they have public read access (you’ll configure that below)
2.**Enable Static Website Hosting**
- Go to the Properties tab of the bucket
- Scroll down to Static website hosting Click Edit Select Enable Enter: Index document: index.html and Error document: error.html
3. **Set Public Read Access Policy**
- Paste the following bucket policy in the Permissions > Bucket Policy section:

<pre>json
Copy
Edit
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::mystaticwerj25/*"
    }
  ] 
}``` </pre>  
4. **Disable Block Public Access**
- If not already done: Go to Permissions > Block public access Click Edit
- Uncheck “Block all public access” Confirm changes

🔔 **You must disable block public access to allow public policies.**

5. **select at your bucket Properties > Static website hosting, and you’ll see a URL like this:**

Copy
Edit
(http://mystaticwerj25.s3-website-<region>.amazonaws.com)
This is your live site!
