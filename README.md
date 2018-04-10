Alicloud Classic Load Balance Architecture Terraform Module
terraform-alicloud-classic-load-balance
=====================================================================

A terraform module to provide classic load balance architecture in alibaba cloud.

![image](https://github.com/aliyun/terraform-alicloud-classic-load-balance/blob/master/architecture.png)

These types of the module resource are supported:

- [VPC](https://www.terraform.io/docs/providers/alicloud/r/vpc.html)
- [Subnet](https://www.terraform.io/docs/providers/alicloud/r/vswitch.html)
- [Load Balancer](https://www.terraform.io/docs/providers/alicloud/r/slb.html)
- [ECS Instance](https://www.terraform.io/docs/providers/alicloud/r/instance.html)
- [Security Group](https://www.terraform.io/docs/providers/alicloud/r/security_group.html)
- [RDS Instance](https://www.terraform.io/docs/providers/alicloud/r/db_instance.html)
- [RDS Account](https://www.terraform.io/docs/providers/alicloud/r/db_account.html)
- [RDS Database](https://www.terraform.io/docs/providers/alicloud/r/db_database.html)
- [OSS Bucket](https://www.terraform.io/docs/providers/alicloud/r/oss_bucket.html)


----------------------

Usage
-----
You can use this in your terraform template with the following steps.

```
module "classic-load-balance" {
    source = "terraform-alicloud-classic-load-balance"

    alicloud_access_key = "Abc123"
    alicloud_secret_key = "Abc1234"
    region = "cn-beijing"

    vpc_name = "my-new-vpc"
    vswitch_cidrs = ["10.1.2.0/24", "10.1.3.0/24"]

    system_category = "cloud_ssd"
    system_size = "100"

    slb_max_bandwidth = "50"
}
```

Conditional creation
--------------------
This example supports using existing VPC and VSwitches to create ECS and RDS instances conditionally.

### Using existing vpc and vswitches for the cluster.

You can specify the following user-defined arguments:

* vpc_id: A existing vpc ID
* vswitch_ids: List of IDs for several existing vswitches

**Note:** At present, not all availability zone supports launching RDS instance. If you want to using existing vswitches,
you must ensure the specified vswitches can creating RDS instance.

```
module "classic-load-balance" {
    source = "terraform-alicloud-classic-load-balance"

    alicloud_access_key = "Abc123"
    alicloud_secret_key = "Abc1234"
    region = "cn-beijing"

    vpc_id = "vpc-abc12345"
    vswitch_cidrs = ["vsw-abc12345", "vsw-abc54321"]

    system_category = "cloud_ssd"
    system_size = "100"

    slb_max_bandwidth = "50"
}
```

Terraform version
-----------------
Terraform version 0.11.0 or newer is required for this module to work.

Authors
-------
Created and maintained by He Guimin(@xiaozhu36, heguimin36@163.com)

License
-------
Mozilla Public License 2.0. See LICENSE for full details.

Reference
---------
* [Terraform-Provider-Alicloud Github](https://github.com/terraform-providers/terraform-provider-alicloud)
* [Terraform-Provider-Alicloud Release](https://releases.hashicorp.com/terraform-provider-alicloud/)
* [Terraform-Provider-Alicloud Docs](https://www.terraform.io/docs/providers/alicloud/)

