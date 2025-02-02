---
subcategory: "Elemental MediaPackage"
layout: "aws"
page_title: "AWS: aws_media_package_channel"
description: |-
  Provides an AWS Elemental MediaPackage Channel.
---


<!-- Please do not edit this file, it is generated. -->
# Resource: aws_media_package_channel

Provides an AWS Elemental MediaPackage Channel.

## Example Usage

```typescript
// DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
import { Construct } from "constructs";
import { TerraformStack } from "cdktf";
/*
 * Provider bindings are generated by running `cdktf get`.
 * See https://cdk.tf/provider-generation for more details.
 */
import { MediaPackageChannel } from "./.gen/providers/aws/media-package-channel";
class MyConvertedCode extends TerraformStack {
  constructor(scope: Construct, name: string) {
    super(scope, name);
    new MediaPackageChannel(this, "kittens", {
      channelId: "kitten-channel",
      description: "A channel dedicated to amusing videos of kittens.",
    });
  }
}

```

## Argument Reference

This resource supports the following arguments:

* `channelId` - (Required) A unique identifier describing the channel
* `description` - (Optional) A description of the channel
* `tags` - (Optional) A map of tags to assign to the resource. If configured with a provider [`defaultTags` configuration block](https://registry.terraform.io/providers/hashicorp/aws/latest/docs#default_tags-configuration-block) present, tags with matching keys will overwrite those defined at the provider-level.

## Attribute Reference

This resource exports the following attributes in addition to the arguments above:

* `id` - The same as `channelId`
* `arn` - The ARN of the channel
* `hlsIngest` - A single item list of HLS ingest information
    * `ingest_endpoints` - A list of the ingest endpoints
        * `password` - The password
        * `url` - The URL
        * `username` - The username
* `tagsAll` - A map of tags assigned to the resource, including those inherited from the provider [`defaultTags` configuration block](https://registry.terraform.io/providers/hashicorp/aws/latest/docs#default_tags-configuration-block).

## Import

In Terraform v1.5.0 and later, use an [`import` block](https://developer.hashicorp.com/terraform/language/import) to import Media Package Channels using the channel ID. For example:

```typescript
// DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
import { Construct } from "constructs";
import { TerraformStack } from "cdktf";
class MyConvertedCode extends TerraformStack {
  constructor(scope: Construct, name: string) {
    super(scope, name);
  }
}

```

Using `terraform import`, import Media Package Channels using the channel ID. For example:

```console
% terraform import aws_media_package_channel.kittens kittens-channel
```

<!-- cache-key: cdktf-0.20.0 input-749270ff3fa0c6f15341b2b41f6c3363f04071edc7478cee4ebbc36cb5e14a07 -->