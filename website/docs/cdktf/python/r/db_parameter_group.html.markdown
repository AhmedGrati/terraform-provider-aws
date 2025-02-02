---
subcategory: "RDS (Relational Database)"
layout: "aws"
page_title: "AWS: aws_db_parameter_group"
description: |-
  Provides an RDS DB parameter group resource.
---


<!-- Please do not edit this file, it is generated. -->
# Resource: aws_db_parameter_group

Provides an RDS DB parameter group resource. Documentation of the available parameters for various RDS engines can be found at:

* [Aurora MySQL Parameters](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/AuroraMySQL.Reference.html)
* [Aurora PostgreSQL Parameters](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/AuroraPostgreSQL.Reference.html)
* [MariaDB Parameters](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Appendix.MariaDB.Parameters.html)
* [Oracle Parameters](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ModifyInstance.Oracle.html#USER_ModifyInstance.Oracle.sqlnet)
* [PostgreSQL Parameters](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Appendix.PostgreSQL.CommonDBATasks.html#Appendix.PostgreSQL.CommonDBATasks.Parameters)

> **Hands-on:** For an example of the `aws_db_parameter_group` in use, follow the [Manage AWS RDS Instances](https://learn.hashicorp.com/tutorials/terraform/aws-rds?in=terraform/aws&utm_source=WEBSITE&utm_medium=WEB_IO&utm_offer=ARTICLE_PAGE&utm_content=DOCS) tutorial on HashiCorp Learn.

~> **NOTE:** After applying your changes, you may encounter a perpetual diff in your Terraform plan
output for a `parameter` whose `value` remains unchanged but whose `apply_method` is changing
(e.g., from `immediate` to `pending-reboot`, or `pending-reboot` to `immediate`). If only the
apply method of a parameter is changing, the AWS API will not register this change. To change
the `apply_method` of a parameter, its value must also change.

## Example Usage

### Basic Usage

```python
# DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
from constructs import Construct
from cdktf import TerraformStack
#
# Provider bindings are generated by running `cdktf get`.
# See https://cdk.tf/provider-generation for more details.
#
from imports.aws.db_parameter_group import DbParameterGroup
class MyConvertedCode(TerraformStack):
    def __init__(self, scope, name):
        super().__init__(scope, name)
        DbParameterGroup(self, "default",
            family="mysql5.6",
            name="rds-pg",
            parameter=[DbParameterGroupParameter(
                name="character_set_server",
                value="utf8"
            ), DbParameterGroupParameter(
                name="character_set_client",
                value="utf8"
            )
            ]
        )
```

### `create_before_destroy` Lifecycle Configuration

The [`create_before_destroy`](https://developer.hashicorp.com/terraform/language/meta-arguments/lifecycle#create_before_destroy)
lifecycle configuration is necessary for modifications that force re-creation of an existing,
in-use parameter group. This includes common situations like changing the group `name` or
bumping the `family` version during a major version upgrade. This configuration will prevent destruction
of the deposed parameter group while still in use by the database during upgrade.

```python
# DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
from cdktf import TerraformResourceLifecycle
from constructs import Construct
from cdktf import TerraformStack
#
# Provider bindings are generated by running `cdktf get`.
# See https://cdk.tf/provider-generation for more details.
#
from imports.aws.db_instance import DbInstance
from imports.aws.db_parameter_group import DbParameterGroup
class MyConvertedCode(TerraformStack):
    def __init__(self, scope, name, *, instanceClass):
        super().__init__(scope, name)
        example = DbParameterGroup(self, "example",
            family="postgres13",
            lifecycle=TerraformResourceLifecycle(
                create_before_destroy=True
            ),
            name="my-pg",
            parameter=[DbParameterGroupParameter(
                name="log_connections",
                value="1"
            )
            ]
        )
        aws_db_instance_example = DbInstance(self, "example_1",
            apply_immediately=True,
            parameter_group_name=example.name,
            instance_class=instance_class
        )
        # This allows the Terraform resource name to match the original name. You can remove the call if you don't need them to match.
        aws_db_instance_example.override_logical_id("example")
```

## Argument Reference

This resource supports the following arguments:

* `name` - (Optional, Forces new resource) The name of the DB parameter group. If omitted, Terraform will assign a random, unique name.
* `name_prefix` - (Optional, Forces new resource) Creates a unique name beginning with the specified prefix. Conflicts with `name`.
* `family` - (Required, Forces new resource) The family of the DB parameter group.
* `description` - (Optional, Forces new resource) The description of the DB parameter group. Defaults to "Managed by Terraform".
* `parameter` - (Optional) A list of DB parameters to apply. Note that parameters may differ from a family to an other. Full list of all parameters can be discovered via [`aws rds describe-db-parameters`](https://docs.aws.amazon.com/cli/latest/reference/rds/describe-db-parameters.html) after initial creation of the group.
* `tags` - (Optional) A map of tags to assign to the resource. If configured with a provider [`default_tags` configuration block](https://registry.terraform.io/providers/hashicorp/aws/latest/docs#default_tags-configuration-block) present, tags with matching keys will overwrite those defined at the provider-level.

Parameter blocks support the following:

* `name` - (Required) The name of the DB parameter.
* `value` - (Required) The value of the DB parameter.
* `apply_method` - (Optional) "immediate" (default), or "pending-reboot". Some
    engines can't apply some parameters without a reboot, and you will need to
    specify "pending-reboot" here.

## Attribute Reference

This resource exports the following attributes in addition to the arguments above:

* `id` - The db parameter group name.
* `arn` - The ARN of the db parameter group.
* `tags_all` - A map of tags assigned to the resource, including those inherited from the provider [`default_tags` configuration block](https://registry.terraform.io/providers/hashicorp/aws/latest/docs#default_tags-configuration-block).

## Import

In Terraform v1.5.0 and later, use an [`import` block](https://developer.hashicorp.com/terraform/language/import) to import DB Parameter groups using the `name`. For example:

```python
# DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
from constructs import Construct
from cdktf import TerraformStack
class MyConvertedCode(TerraformStack):
    def __init__(self, scope, name):
        super().__init__(scope, name)
```

Using `terraform import`, import DB Parameter groups using the `name`. For example:

```console
% terraform import aws_db_parameter_group.rds_pg rds-pg
```

<!-- cache-key: cdktf-0.20.0 input-58d3afb77ce85c7eccf039e1c08d533c541b3a0e93a559083e86605494ac1352 -->