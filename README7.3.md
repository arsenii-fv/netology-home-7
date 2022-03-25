## Домашнее задание к занятию "7.3. Основы и принцип работы Терраформ"

1.
````bash
vagrant@netology1:~/git_net7.2/devops-netology/terraform$ terraform workspace list
  default
  prod
* stage
````
2. В связи с международными событиями регистрация в облаке Amazon с карт зарегитрированных на территории Российской Федерации 
и Белоруссии заблокированна. На второй вопрос ответ предоставил в облаке yandex cloud но работу с workspaces yandex не поддерживает.
Необходимо разделять воркспейсы по каталогам.
````yaml
vagrant@netology1:~/git_net7.2/devops-netology/terraform/terraform.tfstate.d/prod$ terraform116 plan

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the
following symbols:
  + create

Terraform will perform the following actions:

  # yandex_compute_instance.virt-1 will be created
  + resource "yandex_compute_instance" "virt-1" {
      + created_at                = (known after apply)
      + folder_id                 = (known after apply)
      + fqdn                      = (known after apply)
      + hostname                  = (known after apply)
      + id                        = (known after apply)
      + metadata                  = {
          + "user-data" = <<-EOT
                #cloud-config
                users:
                  - name: guest
                    groups: sudo
                    shell: /bin/bash
                    sudo: ['ALL=(ALL) NOPASSWD:ALL']
                    ssh-authorized-keys:
                      - ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDolUJc7b1oehOobrPFJjK4XCh4fluwuIRIW0crPIum1pAQT1+si45APGzJegluuQQkWbaOiAKR1GFcs5XB/3lM1Ern8qHLc3DfmegRufVUof73Bjh7WEIpFNwrVmZfikcwjUYue8/cZqN/DrZyxD1F4YnxDHeufKB30EuuJfWFTPwq+mTw7kkvlSFffx2RJb5G3OnH23NwXGu5INBqQ3vA6hPct66AdwpdR3mJqW9Go3xC3UmIHnK52hwo7KKIrykidURjhAZERNKlfxYsV8pCyqELYqsvOo9rhvLXOwa9Rdt/ELPIBp7eHoiYW/t+n1+9xXa3EX9+NQ/h/ucVk2QT guest@example.com

            EOT
        }
      + name                      = "netology-ter1"
      + network_acceleration_type = "standard"
      + platform_id               = "standard-v1"
      + service_account_id        = (known after apply)
      + status                    = (known after apply)
      + zone                      = (known after apply)

      + boot_disk {
          + auto_delete = true
          + device_name = (known after apply)
          + disk_id     = (known after apply)
          + mode        = (known after apply)

          + initialize_params {
              + block_size  = (known after apply)
              + description = (known after apply)
              + image_id    = "fd804nmi5gak42ae1dcq"
              + name        = (known after apply)
              + size        = (known after apply)
              + snapshot_id = (known after apply)
              + type        = "network-hdd"
            }
        }

      + network_interface {
          + index              = (known after apply)
          + ip_address         = (known after apply)
          + ipv4               = true
          + ipv6               = (known after apply)
          + ipv6_address       = (known after apply)
          + mac_address        = (known after apply)
          + nat                = true
          + nat_ip_address     = (known after apply)
          + nat_ip_version     = (known after apply)
          + security_group_ids = (known after apply)
          + subnet_id          = (known after apply)
        }

      + placement_policy {
          + placement_group_id = (known after apply)
        }

      + resources {
          + core_fraction = 100
          + cores         = 2
          + memory        = 2
        }

      + scheduling_policy {
          + preemptible = (known after apply)
        }
    }

  # yandex_compute_instance.virt-2 will be created
  + resource "yandex_compute_instance" "virt-2" {
      + created_at                = (known after apply)
      + folder_id                 = (known after apply)
      + fqdn                      = (known after apply)
      + hostname                  = (known after apply)
      + id                        = (known after apply)
      + metadata                  = {
          + "user-data" = <<-EOT
                #cloud-config
                users:
                  - name: guest
                    groups: sudo
                    shell: /bin/bash
                    sudo: ['ALL=(ALL) NOPASSWD:ALL']
                    ssh-authorized-keys:
                      - ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDolUJc7b1oehOobrPFJjK4XCh4fluwuIRIW0crPIum1pAQT1+si45APGzJegluuQQkWbaOiAKR1GFcs5XB/3lM1Ern8qHLc3DfmegRufVUof73Bjh7WEIpFNwrVmZfikcwjUYue8/cZqN/DrZyxD1F4YnxDHeufKB30EuuJfWFTPwq+mTw7kkvlSFffx2RJb5G3OnH23NwXGu5INBqQ3vA6hPct66AdwpdR3mJqW9Go3xC3UmIHnK52hwo7KKIrykidURjhAZERNKlfxYsV8pCyqELYqsvOo9rhvLXOwa9Rdt/ELPIBp7eHoiYW/t+n1+9xXa3EX9+NQ/h/ucVk2QT guest@example.com

            EOT
        }
      + name                      = "netology-ter2"
      + network_acceleration_type = "standard"
      + platform_id               = "standard-v1"
      + service_account_id        = (known after apply)
      + status                    = (known after apply)
      + zone                      = (known after apply)

      + boot_disk {
          + auto_delete = true
          + device_name = (known after apply)
          + disk_id     = (known after apply)
          + mode        = (known after apply)

          + initialize_params {
              + block_size  = (known after apply)
              + description = (known after apply)
              + image_id    = "fd804nmi5gak42ae1dcq"
              + name        = (known after apply)
              + size        = (known after apply)
              + snapshot_id = (known after apply)
              + type        = "network-hdd"
            }
        }

      + network_interface {
          + index              = (known after apply)
          + ip_address         = (known after apply)
          + ipv4               = true
          + ipv6               = (known after apply)
          + ipv6_address       = (known after apply)
          + mac_address        = (known after apply)
          + nat                = true
          + nat_ip_address     = (known after apply)
          + nat_ip_version     = (known after apply)
          + security_group_ids = (known after apply)
          + subnet_id          = (known after apply)
        }

      + placement_policy {
          + placement_group_id = (known after apply)
        }

      + resources {
          + core_fraction = 100
          + cores         = 4
          + memory        = 2
        }

      + scheduling_policy {
          + preemptible = (known after apply)
        }
    }

  # yandex_storage_bucket.bucket_stage will be created
  + resource "yandex_storage_bucket" "bucket_stage" {
      + access_key         = "AJERoM3ckBUlOTxl_xpxMji"
      + acl                = "private"
      + bucket             = "arseny"
      + bucket_domain_name = (known after apply)
      + force_destroy      = false
      + id                 = (known after apply)
      + secret_key         = (sensitive value)
      + website_domain     = (known after apply)
      + website_endpoint   = (known after apply)

      + lifecycle_rule {
          + enabled = true
          + id      = "log"
          + prefix  = "terraform.tfstate.d/stage"

          + expiration {
              + days = 90
            }

          + transition {
              + days          = 30
              + storage_class = "COLD"
            }
        }
      + lifecycle_rule {
          + enabled = true
          + id      = "stage"
          + prefix  = "terraform.tfstate.d/stage"

          + expiration {
              + date = "2022-03-21"
            }
        }

      + versioning {
          + enabled = (known after apply)
        }
    }

  # yandex_vpc_network.network-1 will be created
  + resource "yandex_vpc_network" "network-1" {
      + created_at                = (known after apply)
      + default_security_group_id = (known after apply)
      + folder_id                 = (known after apply)
      + id                        = (known after apply)
      + labels                    = (known after apply)
      + name                      = "network1"
      + subnet_ids                = (known after apply)
    }

  # yandex_vpc_network.network-2 will be created
  + resource "yandex_vpc_network" "network-2" {
      + created_at                = (known after apply)
      + default_security_group_id = (known after apply)
      + folder_id                 = (known after apply)
      + id                        = (known after apply)
      + labels                    = (known after apply)
      + name                      = "network2"
      + subnet_ids                = (known after apply)
    }

  # yandex_vpc_subnet.subnet-1 will be created
  + resource "yandex_vpc_subnet" "subnet-1" {
      + created_at     = (known after apply)
      + folder_id      = (known after apply)
      + id             = (known after apply)
      + labels         = (known after apply)
      + name           = "subnet1"
      + network_id     = (known after apply)
      + v4_cidr_blocks = [
          + "192.168.2.0/24",
        ]
      + v6_cidr_blocks = (known after apply)
      + zone           = "ru-central1-a"
    }

  # yandex_vpc_subnet.subnet-2 will be created
  + resource "yandex_vpc_subnet" "subnet-2" {
      + created_at     = (known after apply)
      + folder_id      = (known after apply)
      + id             = (known after apply)
      + labels         = (known after apply)
      + name           = "subnet2"
      + network_id     = (known after apply)
      + v4_cidr_blocks = [
          + "192.168.2.0/24",
        ]
      + v6_cidr_blocks = (known after apply)
      + zone           = "ru-central1-a"
    }

Plan: 7 to add, 0 to change, 0 to destroy.

Changes to Outputs:
  + external_ip_address_virt_1 = (known after apply)
  + external_ip_address_virt_2 = (known after apply)
  + internal_ip_address_virt_1 = (known after apply)
  + internal_ip_address_virt_2 = (known after apply)

───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────

Note: You didn't use the -out option to save this plan, so Terraform can't guarantee to take exactly these actions if you
run "terraform apply" now.
vagrant@netology1:~/git_net7.2/devops-netology/terraform/terraform.tfstate.d/prod$
````
