# mynote-Terraform

* baisc config
* conponent
* provider
* using abstraction and reusable components


## infra as code
provisioning consistent predictable

* code - json , yaml , HCL
* GIT/GIThub
* declarative - noun /imperative-verb
* idempotent consistent
* push pull


* automation
* repeatable
* consistent
* reusable
* documented

paid- terraform cloud/enterprise


conponent
* executable
* configuration file - HCL
* provider plugins - registry.terraform.io
* state data


### terrraform object types
* providers
    * aws, account,region
* resources
    * create - ec2, network , db
* data sources
    * query - zone, ami, template


```haskell=
block_type "label" "name_label"{
    key="value"
    nested_block {
        key ="value"
    }
     
}


#----------------
resource "aws_instance" "web_server"{
    name ="web-server"
    ebs_volume {
        size = 40
    }
}

```

tf object reference 
<resource_type>.<name_label>.<attribute>










