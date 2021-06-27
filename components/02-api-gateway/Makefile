MAKE_ARGS:=--profile ${AWS_PROFILE} --region ${AWS_REGION}

# nonproduction/production, defaults to nonproduction
ENV_TYPE?=nonproduction

STACK_NAME:=$(NAMESPACE)-api-gateway

package:
	aws cloudformation package --template-file stack.yaml --s3-bucket $(CFN_BUCKET) --output-template-file packaged.yaml $(MAKE_ARGS)

deploy: package
	aws cloudformation deploy --stack-name $(STACK_NAME) --template-file packaged.yaml --parameter-overrides Namespace=$(NAMESPACE) --capabilities CAPABILITY_IAM $(MAKE_ARGS)

delete-stack:
	aws cloudformation delete-stack --stack-name $(STACK_NAME) $(MAKE_ARGS)
