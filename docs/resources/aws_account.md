---
page_title: "controltower_aws_account Resource - terraform-provider-controltower"
subcategory: ""
description: |-
  Provides an AWS account resource via Control Tower.
---

# Resource `controltower_aws_account`

Provides an AWS account resource via Control Tower.

## Example Usage

```terraform
resource "controltower_aws_account" "account" {
  name                = "Example Account"
  email               = "aws-admin@example.com"
  organizational_unit = "Sandbox"

  sso {
    first_name = "John"
    last_name  = "Doe"
    email      = "john.doe@example.com"
  }

  lifecycle {
    prevent_destroy = true
  }
}
```

## Schema

### Required

- **email** (String) Root email of the account.
- **name** (String) Name of the account.
- **organizational_unit** (String) Name of the Organizational Unit under which the account resides.
- **sso** (Block List, Min: 1, Max: 1) Assigned SSO user settings. (see [below for nested schema](#nestedblock--sso))

### Optional

- **id** (String) The ID of this resource.
- **provisioned_product_name** (String) Name of the service catalog product that is provisioned. Defaults to a slugified version of the account name.
- **tags** (Map of String) Key-value map of resource tags for the account.

### Read-only

- **account_id** (String) ID of the AWS account.

<a id="nestedblock--sso"></a>
### Nested Schema for `sso`

Required:

- **email** (String) Email address of the user. If you use automatic provisioning this email address should already exist in AWS SSO.
- **first_name** (String) First name of the user.
- **last_name** (String) Last name of the user.

