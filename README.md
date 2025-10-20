# Static Website Hosting/Deployment to AWS S3

# Introduction
In this project, we will create and configure a simple static website. We will go through configuring that static website with a custom error page. This will demonstrate how to create a cost-efficient website hosting for sites that consist of files like HTML, CSS, JavaScript, fonts, and images.

Solution
Log in to the live AWS environment and select your prefered region

Create S3 Bucket
In a new browser tab, navigate to the GitHub repository for the code.

Select the error.html file.

Above the code area, click Raw.

Right-click and select Save Page As, and save the file as error.html.

Note: If you are using Safari as your web browser, ensure you remove .txt from the end of the filename. Also, ensure the Format is Page Source. When asked whether you want to save the file as plain text, click Don't append.

Repeat this for the index.html file.

In the AWS Management Console, navigate to S3.

Click Create bucket.

Set the following values:

Bucket name: my-bucket- with the AWS account ID or another series of numbers at the end to make it globally unique
Region: US East (N. Virginia) us-east-1
In the Block Public Access settings for this bucket section, un-check Block all public access.

Ensure all four permissions restrictions beneath it are also un-checked.
Check the box to acknowledge that turning off all public access might result in the bucket and its objects becoming public.

Leave the rest of the settings as their defaults.

Click Create bucket.

Click the bucket name.

Click Upload.

Click Add files, and upload the error.html and index.html files you previously saved from GitHub.

Leave the rest of the settings as their defaults.

Click Upload.

Click Close in the upper right.

Enable Static Website Hosting
Click the Properties tab.

Scroll to the bottom of the screen to find the Static website hosting section.

On the right in the Static website hosting section, click Edit.

On the Edit static website hosting page, set the following values:

Static website hosting: Select Enable.
Hosting type: Select Host a static website.
Index document: Enter index.html.
Error document: Enter error.html.
Click Save changes.

In the Static website hosting section, open the listed endpoint URL in a new browser tab. Once opened, you'll see a 403 Forbidden error message.

Apply Bucket Policy
Back in S3, click the Permissions tab.

In the Bucket policy section, click Edit.

Above the code entry box, copy the bucket ARN.

On the right, click Policy generator.

Select the following values:

Select Type of Policy: Select S3 Bucket Policy.
Effect: Select Allow.
Principal: Enter *.
Actions: Select GetObject.
Amazon Resource Name (ARN): Paste the name you added earlier followed by /* so the policy applies to all objects within the bucket.
Click Add Statement > Generate Policy.

Copy the displayed policy, and go back to the bucket policy screen and paste the JSON. You can ignore any errors.

Click Save changes.

Refresh the browser tab with the static website (the endpoint URL you opened earlier). This time, the site should load correctly.

Add a / at the end of the URL and some random letters (anything that's knowingly an error). This will display your error.html page.

Conclusion