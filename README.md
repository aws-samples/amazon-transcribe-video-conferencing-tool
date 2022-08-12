
## Amazon Transcribe Video Conferencing Tool
This repo contain the CloudFormation templates required to deploy a solution with the following capabilities:

 1. Transcribe a video input
 2. Redact personally identifiable information and remove it from the transcript
 3. Process the input file to mute personally identifiable information
 4. Generate a non-extractive video summary

**Services used:**
1.	Amazon S3
2.	AWS Lambda
3.	Amazon Transcribe
4. Amazon SageMaker
Packages used:
1.	FFMPEG for video processing via the [AWS Serverless Repo](https://serverlessrepo.aws.amazon.com/applications)
2. In order to make the process automated, service calls were made inside Lambda functions using the AWS Python SDK [Boto3](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html)

### Redaction
The fulll solution can be provisioned by downloading and running the cloudformation template under "cf-redaction". In order to run this template, go to your AWS account and find the CloudFormation console. Then select "Create Stack" with new resources and upload the template. Before deploying this code, some things to note about this template:
* The template will ask you to specify the names of three S3 buckets: Input Bucket, Output Bucket, and Transcript Bucket. These parameters are designed to allow you to better monitor the solution after its deployment. As a result, do not provide names of buckets that already exist within your account. Rather, provide names of buckets you wish to be created.
* The function will also ask for an FFmpeg build. This parameter will accept float values and will determine the build of FFmpeg to pull from the AWS Serverless Repo. If you wish to specify a build version, review the versions and their associated version numbers [here](Before deploying this code, some things to note about this template:
* The template will ask you to specify the names of three S3 buckets: Input Bucket, Output Bucket, and Transcript Bucket. These parameters are designed to allow you to better monitor the solution after its deployment. As a result, do not provide names of buckets that already exist within your account. Rather, provide names of buckets you wish to be created.
* The function will also ask for an FFmpeg build. This parameter will accept float values and will determine the build of FFmpeg to pull from the AWS Serverless Repo. If you wish to specify a build version, review the versions and their associated version numbers [here](https://serverlessrepo.aws.amazon.com/applications/us-east-1/145266761615/ffmpeg-lambda-layer). Otherwise, the default value of 1.0.0 will pull the latest version (as of the writing of this document).
* As in this document, the solution will defer to Full Access for all IAM permissions. You may want to reduce the permissibility of these permissions after deploying this solution. As a best practice, you will want to reduce the permissibility to only allow actions absolutely necessary on the resources required. More information about configuring these permissions after you add in desired capabilities can be found [here](https://aws.amazon.com/iam/features/manage-permissions/#:~:text=Permissions%20let%20you%20specify%20access,grant%20them%20your%20desired%20permissions.).





