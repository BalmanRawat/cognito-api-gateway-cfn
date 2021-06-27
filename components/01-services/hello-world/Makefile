MAKE_ARGS=--profile $(AWS_PROFILE) --region $(AWS_REGION)

# nonproduction/production, defaults to nonproduction
ENV_TYPE?=nonproduction

STACK_NAME:=$(NAMESPACE)-hello-world-lambda

local:
	sam local start-lambda --template-file stack.yaml

package:
	sam package --template-file stack.yaml --output-template-file packaged.yaml --s3-bucket $(CFN_BUCKET) $(MAKE_ARGS)

deploy: package
	sam deploy --template-file packaged.yaml --stack-name ${STACK_NAME} \
		--capabilities CAPABILITY_IAM $(MAKE_ARGS) \
		--parameter-overrides EnvironmentType=$(ENV_TYPE) Namespace=$(NAMESPACE)
