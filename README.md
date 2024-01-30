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
