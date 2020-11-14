# codepipeline_cft_s3_demo
s3cft.yml shows code pipeline with cloud formation as source

## Description
I followed the below two articles to experiment with code pipeline

<p>https://www.youtube.com/watch?v=LHz04uN-wI0</p>
<p>https://www.youtube.com/watch?v=9hqbzuN--sk</p>


# create a new vpc with the first cft script, then run the second script to create a load balanced EB environment

<p>aws cloudformation create-stack --stack-name faiz-vpc --template-body file://IAAS_CloudFormation_NAT_Instances.json --capabilities CAPABILITY_NAMED_IAM --region eu-west-2</p>
<p>aws cloudformation create-stack --stack-name test-dev-resources --template-body file://NodeJSEB_cft.yml --parameters  file://NodeJSEB_cft-param.json --capabilities CAPABILITY_NAMED_IAM --region eu-west-2</p>