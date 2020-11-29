# codepipeline_cft_s3_demo
s3cft.yml shows code pipeline with cloud formation as source

## Description
I followed the below two articles to experiment with code pipeline

<p>https://www.youtube.com/watch?v=LHz04uN-wI0</p>
<p>https://www.youtube.com/watch?v=9hqbzuN--sk</p>


# create a new vpc with the first cft script, then run the second script to create a load balanced Elastic Beanstalk environment

## Description
* The first script creates a new VPC with two private and two public subnets, with nat instances in each public subnets.
* The second script creates an EB stack in the vpc with a public ALB and private load balanced instances.

<p>aws cloudformation create-stack --stack-name custom-vpc-resources-cft --template-body file://IAAS_CloudFormation_NAT_Instances.json --capabilities CAPABILITY_NAMED_IAM --region eu-west-2</p>
<p>aws cloudformation create-stack --stack-name pipeline-resources --template-body file://NodeJSEB_cft.yml --parameters file://NodeJSEB_cft-param.json --capabilities CAPABILITY_NAMED_IAM --region eu-west-2</p>


# File codepipeline_with_cfn_as_deployment_provider.yml creates a codepipeline which pulls the code from Github via codestar connection, and uses Cloudformation to create project resources from the passed yml file. Any further changes to any file in the Github will trigger the pipeline to deploy resources from changed yml file.

#Description
* aws cloudformation create-stack --stack-name faiz-codepipeline-stack --template-body file://codepipeline_with_cfn_as_deployment_provider.yml --parameters ParameterKey="PipelineName",ParameterValue="faiz-pipeline4" ParameterKey="TemplateFileName",ParameterValue="s3cft.yml" --capabilities CAPABILITY_NAMED_IAM --region eu-west-2

* aws cloudformation create-stack --stack-name faiz-codepipeline-stack --template-body file://codepipeline_with_cfn_as_deployment_provider.yml --parameters ParameterKey="PipelineName",ParameterValue="faiz-pipeline4" ParameterKey="TemplateFileName",ParameterValue="IAAS_CloudFormation_NAT_Instances.json" --capabilities CAPABILITY_NAMED_IAM --region eu-west-2