# AWS cloudformation and object upload/download API

This project involves setting up an AWS CloudFormation stack using the lp2miniproject.yml template, which creates an S3 bucket to be used for the LP2 Mini Project. Additionally, it includes an Express.js server (index.js) that interacts with the S3 bucket for file uploads and downloads. Below are the instructions and information to set up and run this project.

## CloudFormation Stack Setup
Template: Use the lp2miniproject.yml CloudFormation template to create the necessary AWS resources. This template defines an S3 bucket named lp2miniproject.

yaml
```
AWSTemplateFormatVersion: '2010-09-09'
Resources:
  S3Bucket:
    Type: AWS::S3::Bucket
    Description: S3 Bucket for LP2 Mini Project
    Properties:
      BucketName: lp2miniproject
Outputs:
  S3BucketName:
    Description: Name of the S3 Bucket
    Value: !Ref S3Bucket
```
Stack Creation: Use AWS CloudFormation to create a stack using the provided template. Ensure that the stack creation is successful and note down the S3 bucket name created during this process.

## Server Setup
Environment Variables: Set up the necessary environment variables in a .env file in the root directory of the project. Replace the placeholder values with your actual AWS credentials and bucket information.

```
AWS_BUCKET_NAME=your_bucket_name
AWS_BUCKET_REGION=your_bucket_region
AWS_ACCESS_KEY=your_access_key
AWS_SECRET_KEY=your_secret_key
```
Dependencies Installation: Install the required Node.js dependencies using npm or yarn.

```
npm install
```
# or
```
yarn install
```
Starting the Server: Run the Express.js server using the following command:

```
node index.js
```
## Server Endpoint:

### File Upload:

POST http://localhost:5000/file with a form-data body containing a file to upload. The key for the file should be image.
Returns key to access object in s3 bucket.

### File Download:

GET http://localhost:5000/file/{key}, where {key} is the key of the file stored in the S3 bucket.
The server will retrieve the file from the S3 bucket and stream it as a response.

## Notes
Ensure that your AWS credentials have the necessary permissions to access the S3 bucket created in the CloudFormation stack.
This setup assumes you have Node.js and npm (or yarn) installed on your system.
Feel free to reach out if you encounter any issues or need further assistance!
