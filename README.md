# SageMaker BERT Endpoint
The following project will demonstrate the process of deploying a BERT model fine-tuned on the SQuAD dataset provided by HuggingFace. The model will be deployed to an Amazon SageMaker PyTorch endpoint. This process makes use of Amazon SageMaker, CloudFormation, Elastic Container Service (ECS) and the HuggingFace transformers library.

## Prerequisites
* An AWS Account with an IAM Execution Role for the SageMaker Notebook Instance which can be created using `cloudformation/sagemaker-notebook-role.yaml` CloudFormation template.
* An appropriate SageMaker Notebook Instance limit. A request for a service limit increase can raised by following [this process](https://docs.aws.amazon.com/deepcomposer/latest/devguide/deepcomposer-service-limit.html).

## Getting Started
The easiest way to get started is to spin up an Amazon SageMaker notebook instance using the *SageMaker Notebook Role* that you previously created. You can select a smaller instance such as the `ml.t2.medium` for this step. The process of creating a SageMaker Notebook instance is described [here](https://docs.aws.amazon.com/sagemaker/latest/dg/gs-setup-working-env.html).

The repository can be cloned via the following command.
```
git clone https://github.com/nialdaly/sagemaker-bert-endpoint.git
```

## Resource Cleanup
Any resources created in this project can be simply removed by destroying the CloudFormation stacks that you created using the CloudFormation console. It can also be deleted via the aws cli using the following command.
```
aws cloudformation delete-stack --stack-name lambda-bert-endpoint-stack
```

```
aws cloudformation delete-stack --stack-name sagemaker-bert-endpoint-stack
```

The SageMaker Notebook instance must be terminated yourself. **Remember to stop the instance if you aren't using it as you will be charged otherwise.**

The CloudFormation stack used to create the *SageMaker-Notebook-Role* can be deleted with the following command:
```
aws cloudformation delete-stack --stack-name sagemaker-notebook-role-stack
```

## Additional Resources
- [SageMaker Pre-built Containers](https://docs.aws.amazon.com/sagemaker/latest/dg/pre-built-containers-frameworks-deep-learning.html)
- [BERT Deployment on SageMaker](https://aws.amazon.com/blogs/machine-learning/fine-tuning-a-pytorch-bert-model-and-deploying-it-with-amazon-elastic-inference-on-amazon-sagemaker/)
- [Lambda Inline Code - CloudFormation](https://github.com/awslabs/aws-cloudformation-templates/blob/master/aws/services/CloudFormation/MacrosExamples/PyPlate/python.yaml)