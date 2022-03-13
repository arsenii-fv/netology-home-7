## Домашнее задание к занятию "7.2. Облачные провайдеры и синтаксис Terraform."

### Задача 1 (вариант с AWS). Регистрация в aws и знакомство с основами (необязательно, но крайне желательно).
````bash
vagrant@netology1:~$ aws configure list
      Name                    Value             Type    Location
      ----                    -----             ----    --------
   profile                <not set>             None    None
access_key     ****************TRW3 shared-credentials-file
secret_key     ****************yRrm shared-credentials-file
    region                eu-west-3      config-file    ~/.aws/config
````
````

1. При помощи Packer можно создать свой образ Ami, а Terraform разворачивает инстанс используя наш образ.

[Ссылканаmain.tf]:(https://github.com/arsenii-fv/netology-home-7/blob/60051452a2d03aa95414337701e24bed256648f1/main.tf)


