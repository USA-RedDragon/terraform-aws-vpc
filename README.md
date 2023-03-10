# terraform-aws-dynamodb-service-roles

The module creates the following service linked roles:
- AWSServiceRoleForDynamoDBReplication
- AWSServiceRoleForDynamoDBKinesisDataStreamsReplication
- AWSServiceRoleForApplicationAutoScaling_DynamoDBTable

## Prerequisites
The service linked roles must not exit in the AWS account prior applying the configuration, otherwise execution will fail.

## Usage

```hcl
## Creates linked roles needed by dynamodb-kms module
## The service linked roles must exist before running the module.
module "dynamodb_service_roles" {
source = "tfe.preprod.tlz.svbank.com/svb/dynamodb-service-roles/aws"
tags   = local.tags
}
```



## Providers

| Name | Version |
|------|---------|
| aws | ~> 3.74.1 |


## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_tags"></a> [tags](#input_tags) | A map of tags to tag the service link roles | `map(any)` | n/a | yes |
| <a name="input_custom_suffix"></a> [custom_suffix](#input_custom_suffix) | Additional string appended to the role name. Not all AWS services support custom suffixes | `string` | `null` | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_dynamodb_autoscaling_service_role_arn"></a> [dynamodb_autoscaling_service_role_arn](#output_dynamodb_autoscaling_service_role_arn) | ARN of service link role dynamodb.application-autoscaling.amazonaws.com/AWSServiceRoleForApplicationAutoScaling_DynamoDBTable |
| <a name="output_dynamodb_autoscaling_service_role_name"></a> [dynamodb_autoscaling_service_role_name](#output_dynamodb_autoscaling_service_role_name) | Name of service link role dynamodb.application-autoscaling.amazonaws.com/AWSServiceRoleForApplicationAutoScaling_DynamoDBTable |
| <a name="output_dynamodb_kinesis_replication_service_role_arn"></a> [dynamodb_kinesis_replication_service_role_arn](#output_dynamodb_kinesis_replication_service_role_arn) | ARN of service link role kinesisreplication.dynamodb.amazonaws.com/AWSServiceRoleForDynamoDBKinesisDataStreamsReplication |
| <a name="output_dynamodb_kinesis_replication_service_role_name"></a> [dynamodb_kinesis_replication_service_role_name](#output_dynamodb_kinesis_replication_service_role_name) | Name of service link role kinesisreplication.dynamodb.amazonaws.com/AWSServiceRoleForDynamoDBKinesisDataStreamsReplication |
| <a name="output_dynamodb_replication_service_role_arn"></a> [dynamodb_replication_service_role_arn](#output_dynamodb_replication_service_role_arn) | ARN of replication.dynamodb.amazonaws.com/AWSServiceRoleForDynamoDBReplication |
| <a name="output_dynamodb_replication_service_role_name"></a> [dynamodb_replication_service_role_name](#output_dynamodb_replication_service_role_name) | Name of service link role replication.dynamodb.amazonaws.com/AWSServiceRoleForDynamoDBReplication |

## Examples
Visit https://wiki.svbank.com/display/TEC4E/dynamodb-service-roles

## Resources

| Name | Type |
|------|------|
| [aws_iam_service_linked_role.dynamodb_autoscaling](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_service_linked_role) | resource |
| [aws_iam_service_linked_role.dynamodb_kinesis_replication](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_service_linked_role) | resource |
| [aws_iam_service_linked_role.dynamodb_replication](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_service_linked_role) | resource |
