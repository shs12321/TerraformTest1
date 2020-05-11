# 명령 프롬프트
'''
# nano ~/.bashrc
PS1="\[\033[32m\] \[\033[34;1m\]\W \[\033[32m\]\[\033[m\]\[\e[91m\]\[\e[00m\]$ "
echo "
export TF_VAR_AWS_ACCESS_KEY="키삭제"
export TF_VAR_AWS_SECRET_KEY="키삭제"
export TF_VAR_AWS_REGION="ap-northeast-2"
">> ~/.bashrc
'''
#default VPC를 웹UI로 만들고 시작
'''
vpc 검색 후 작업 - 기본 VPC생성
'''

#시큐리티그룹 생성

#vars.tf
'''
ap-northeast-1 일본 추가
ap-northeast-2 서울도..
'''

#인스턴스 생성과정
'''
sol1 $ terraform init

Initializing the backend...

Initializing provider plugins...
- Checking for available provider plugins...
- Downloading plugin for provider "aws" (hashicorp/aws) 2.61.0...

The following providers do not have any version constraints in configuration,
so the latest version was installed.

To prevent automatic upgrades to new major versions that may contain breaking
changes, it is recommended to add version = "..." constraints to the
corresponding provider blocks in configuration, with the constraint strings
suggested below.

* provider.aws: version = "~> 2.61"

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.

terraform plan
Refreshing Terraform state in-memory prior to plan...
The refreshed state will be used to calculate this plan, but will not be
persisted to local or remote state storage.

aws_key_pair.mykey: Refreshing state... [id=mykey]
aws_instance.example: Refreshing state... [id=i-062dd535027e8ef8e]

------------------------------------------------------------------------

An execution plan has been generated and is shown below.
Resource actions are indicated with the following symbols:
-/+ destroy and then create replacement

Terraform will perform the following actions:

  # aws_instance.example is tainted, so must be replaced
-/+ resource "aws_instance" "example" {
        ami                          = "ami-03179588b2f59f257"
      ~ arn                          = "arn:aws:ec2:ap-northeast-1:651358851825:instance/i-062dd535027e8ef8e" -> (known after apply)
      ~ associate_public_ip_address  = true -> (known after apply)
      ~ availability_zone            = "ap-northeast-1a" -> (known after apply)
      ~ cpu_core_count               = 1 -> (known after apply)
      ~ cpu_threads_per_core         = 1 -> (known after apply)
      - disable_api_termination      = false -> null
      - ebs_optimized                = false -> null
        get_password_data            = false
      - hibernation                  = false -> null
      + host_id                      = (known after apply)
      ~ id                           = "i-062dd535027e8ef8e" -> (known after apply)
      ~ instance_state               = "running" -> (known after apply)
        instance_type                = "t2.micro"
      ~ ipv6_address_count           = 0 -> (known after apply)
      ~ ipv6_addresses               = [] -> (known after apply)
        key_name                     = "mykey"
      - monitoring                   = false -> null
      + network_interface_id         = (known after apply)
      + outpost_arn                  = (known after apply)
      + password_data                = (known after apply)
      + placement_group              = (known after apply)
      ~ primary_network_interface_id = "eni-076bfe686ddd5e1d2" -> (known after apply)
      ~ private_dns                  = "ip-172-31-46-99.ap-northeast-1.compute.internal" -> (known after apply)
      ~ private_ip                   = "172.31.46.99" -> (known after apply)
      ~ public_dns                   = "ec2-18-181-165-90.ap-northeast-1.compute.amazonaws.com" -> (known after apply)
      ~ public_ip                    = "18.181.165.90" -> (known after apply)
      ~ security_groups              = [
          - "default",
        ] -> (known after apply)
        source_dest_check            = true
      ~ subnet_id                    = "subnet-065d973318b444332" -> (known after apply)
      - tags                         = {} -> null
      ~ tenancy                      = "default" -> (known after apply)
      ~ volume_tags                  = {} -> (known after apply)
      ~ vpc_security_group_ids       = [
          - "sg-0be8d7779b92547fe",
        ] -> (known after apply)

      - credit_specification {
          - cpu_credits = "standard" -> null
        }

      + ebs_block_device {
          + delete_on_termination = (known after apply)
          + device_name           = (known after apply)
          + encrypted             = (known after apply)
          + iops                  = (known after apply)
          + kms_key_id            = (known after apply)
          + snapshot_id           = (known after apply)
          + volume_id             = (known after apply)
          + volume_size           = (known after apply)
          + volume_type           = (known after apply)
        }

      + ephemeral_block_device {
          + device_name  = (known after apply)
          + no_device    = (known after apply)
          + virtual_name = (known after apply)
        }

      ~ metadata_options {
          ~ http_endpoint               = "enabled" -> (known after apply)
          ~ http_put_response_hop_limit = 1 -> (known after apply)
          ~ http_tokens                 = "optional" -> (known after apply)
        }

      + network_interface {
          + delete_on_termination = (known after apply)
          + device_index          = (known after apply)
          + network_interface_id  = (known after apply)
        }

      ~ root_block_device {
          ~ delete_on_termination = true -> (known after apply)
          ~ device_name           = "/dev/xvda" -> (known after apply)
          ~ encrypted             = false -> (known after apply)
          ~ iops                  = 100 -> (known after apply)
          + kms_key_id            = (known after apply)
          ~ volume_id             = "vol-02b54b01e014a1018" -> (known after apply)
          ~ volume_size           = 30 -> (known after apply)
          ~ volume_type           = "gp2" -> (known after apply)
        }
    }

Plan: 1 to add, 0 to change, 1 to destroy.

------------------------------------------------------------------------

Note: You didn't specify an "-out" parameter to save this plan, so Terraform
can't guarantee that exactly these actions will be performed if
"terraform apply" is subsequently run.


terraform apply -auto-approve
aws_key_pair.mykey: Refreshing state... [id=mykey]
aws_instance.example: Creating...
aws_instance.example: Still creating... [10s elapsed]
aws_instance.example: Still creating... [20s elapsed]
aws_instance.example: Provisioning with 'file'...
aws_instance.example: Still creating... [30s elapsed]
aws_instance.example: Still creating... [40s elapsed]
aws_instance.example: Still creating... [50s elapsed]
aws_instance.example: Still creating... [1m0s elapsed]
aws_instance.example: Still creating... [1m10s elapsed]
aws_instance.example: Still creating... [1m20s elapsed]
aws_instance.example: Still creating... [1m39s elapsed]
aws_instance.example: Still creating... [1m49s elapsed]
aws_instance.example: Still creating... [1m59s elapsed]
aws_instance.example: Still creating... [2m9s elapsed]
aws_instance.example: Still creating... [2m19s elapsed]
aws_instance.example: Still creating... [2m29s elapsed]
aws_instance.example: Still creating... [2m39s elapsed]
aws_instance.example: Still creating... [2m49s elapsed]
aws_instance.example: Still creating... [2m59s elapsed]
aws_instance.example: Still creating... [3m9s elapsed]
aws_instance.example: Still creating... [3m19s elapsed]
aws_instance.example: Still creating... [3m29s elapsed]
^CInterrupt received.
Please wait for Terraform to exit or data loss may occur.
Gracefully shutting down...
Stopping operation...


Apply complete! Resources: 0 added, 0 changed, 0 destroyed.

            "public_ip": "15.164.95.28"
'''
#TEST과정 :
'''
webpage접속 : 인스턴스의 pulbic IP확인.

명령줄 : set|grep TF_VAR
'''
