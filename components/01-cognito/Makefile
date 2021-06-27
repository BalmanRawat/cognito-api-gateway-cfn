MAKE_ARGS=--profile $(AWS_PROFILE) --region $(AWS_REGION)

# nonproduction/production, defaults to nonproduction
ENV_TYPE?=nonproduction

STACK_NAME:=$(NAMESPACE)-cognito-userpool

create-stack:
	aws cloudformation create-stack --stack-name $(STACK_NAME) --template-body file://stack.yaml --parameters ParameterKey=Namespace,ParameterValue=$(NAMESPACE) $(MAKE_ARGS)

update-stack:
	aws cloudformation update-stack --stack-name $(STACK_NAME) --template-body file://stack.yaml --parameters ParameterKey=Namespace,ParameterValue=$(NAMESPACE) $(MAKE_ARGS)

delete-stack:
	aws cloudformation delete-stack --stack-name $(STACK_NAME) $(MAKE_ARGS)
