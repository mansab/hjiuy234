Based on the fact that I cloned the project from github I decided to set up two [github action](https://github.com/features/actions) workflows which live in the `.github-workflows` dir. If there is a need to run these tasks locally I would recommend [act](https://github.com/nektos/act).
If you want to debug the individual steps you can run every single command (prefixed via `- run:`) on your local Linux terminal.

At the moment there are two points where manual action needs to be taken:
* AWS credentials needs to be set up manually
* kubernetes secret needs to be set up manually

#### AWS credetials:
If you don't have an AWS Access Credentials, create your AWS Access Key ID and Secret Access Key by navigating to your [service credentials](https://console.aws.amazon.com/iam/home?#/security_credentials) in the IAM service on AWS. Click "Create access key" here and download the file. This file contains your access credentials.  
You need then to create [github secrets](https://docs.github.com/en/actions/reference/encrypted-secrets#creating-encrypted-secrets-for-a-repository):
* take as value your credentials
* the keys should match the given ones on the workflow files (`AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY`)
* an alternative to the latter point is to pass the secrets [over to act](https://github.com/nektos/act#secrets)

#### Kubernetes secret
As soon as your cluster is set up you need to create a secret:  
```bash
kubectl create secret generic newsFeedServiceToken --from-literal=newsFeedServiceToken=YOUr_SUPER_SECRET_NEWSFEED_SERVICE_TOKEN
```
