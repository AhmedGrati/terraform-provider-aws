---
subcategory: "Redshift"
layout: "aws"
page_title: "AWS: aws_redshift_subnet_group"
description: |-
  Provides details about a specific redshift subnet_group
---


<!-- Please do not edit this file, it is generated. -->
# Data Source: aws_redshift_subnet_group

Provides details about a specific redshift subnet group.

## Example Usage

```typescript
// DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
import { Construct } from "constructs";
import { Token, TerraformStack } from "cdktf";
/*
 * Provider bindings are generated by running `cdktf get`.
 * See https://cdk.tf/provider-generation for more details.
 */
import { DataAwsRedshiftSubnetGroup } from "./.gen/providers/aws/data-aws-redshift-subnet-group";
class MyConvertedCode extends TerraformStack {
  constructor(scope: Construct, name: string) {
    super(scope, name);
    new DataAwsRedshiftSubnetGroup(this, "example", {
      name: Token.asString(awsRedshiftSubnetGroupExample.name),
    });
  }
}

```

## Argument Reference

This data source supports the following arguments:

* `name` - (Required) Name of the cluster subnet group for which information is requested.

## Attribute Reference

This data source exports the following attributes in addition to the arguments above:

* `arn` - ARN of the Redshift Subnet Group name.
* `description` - Description of the Redshift Subnet group.
* `id` - Redshift Subnet group Name.
* `subnetIds` - An array of VPC subnet IDs.
* `tags` - Tags associated to the Subnet Group

<!-- cache-key: cdktf-0.20.0 input-1814cef40fea2151683ed9925569f34cf19ac6b05b2de4b553e90c473dc2df91 -->