# 멀티인스턴스 적용 instance.tf
'''
esource "aws_instance" "example" {
  count         = var.instance_count
'''

#vars
'''
variable "instance_count" {
  default = "4"
}

'''
