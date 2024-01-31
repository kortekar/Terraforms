# ❗️Terraforms 👨🏻‍💻
### ✅ Baisc structure should start with provider 
    provider "aws" {
      region = "region of server "
      access_key = "my access key"
      secret_key = "my secret key"
    }
    // to get those key goto aws profile -> my scurity credentials -> create access key copy and paste here
### ✅ main syntax would be 👇🏻
    resources "<provider>_<resource_type>" "name" {
    config option 
    key = " value "
    key2 = " value "
    }
### ✅ resources and its type💁🏻  ( suggestion : open terraforms documentation you'll get examples )
    resources "aws_instance"  "Name_of_your_choice" {
    ami = < you'll get it in cloud console Amzon machine image code(AMI) ex: ami-567890123 >
    instance_type = "your_choice ex: t2micro"
    
    tags{ 
        name = " Give any name i'm gonna call it ubunu server "   }
    }
### ✅ now open terminal in project folder run commands below 👇🏻
    terraform init
    terraform plan  
### ✅ second command gives some extra code and give a blue print what else we can add in this code 👆🏻
### ✅ to run the code 👇🏻
    terraform apply
### ✅❗️❗️❗️❗️❗️❗️❗️ "terraform destroy" command will destroy the instance 🔪 even the absence of resources and other will act as destroy




# 🪢👨🏻‍💻Creating a VPC ( virtual private cloud ) and working on subnet
    resource "aws_vpc" "first-vpc" {
    cidr_block = "10.0.0.0/16"
    tags = {
        Name = "production"
      }
    }


### subnet
    resource "aws_subnet" "subnet-1" {
    vpc_id     = aws_vpc.main.id // just copy "aws_vpc" "first-vpc" from above resource alter

    cidr_block = "10.0.1.0/24"

    tags = {
        Name = "production-subnet"
      }
    }










# Final Code❗️❗️❗️❗️❗️
    provider "aws" {
      region = "us-north-1"
      access_key = "my access key"
      secret_key = "my secret key"
    }
    resources "aws_instance" "my-first-server" {
        ami =" "
        instance_type = "t2.micro"
        tags = {
            Name = "HelloWorld"
        }
    }
    resource "aws_vpc" "main" {
    cidr_block = "10.0.0.0/16"
    tags = {
        Name = "production"
      }
    }
    resource "aws_subnet" "subnet-1" {
    vpc_id     = aws_vpc.main.id
    cidr_block = "10.0.1.0/24"

    tags = {
        Name = "production-subnet"
      }
    }

### this is enough to create an instance in AWS👍✌️

# ✅ 🪢 want to learn in proper way check below
    provider "aws"{
    region = "us-east-1"
    access_key = "askjhfljasdfhgkldsjh"
    secret_key = "23jkldsjhfkjhkdsfahj/fg"
    }
    
    # 1. creating VPC
    resource "aws_vpc" "prod-vpc"{
    cidr_block ="10.0.0.0/16"
        tags = {
            Name = "production"
        }
    }

    
    # 2. Create Internet Gateway
    resource "aws_internet_gateway" "gw"{
    vpc_id = aws_vpc.prod-vpc.id
    }

    
    # 3. creating Custom Route table 
    resource "aws_route_table" "prod-route-table" {
    vpc_id = aws_vpc.prod-vpc.id

    route {
    cidr_block = ""
    gateway_id = aws_internet_gateway.example.id
    }

    route {
    ipv6_cidr_block        = "::/0"
    egress_only_gateway_id ="${aws_egress_only_internet_gateway.example.id}"
      }

    tags = {
        Name = "production"
      }
    }












