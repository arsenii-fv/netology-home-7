## Домашнее задание к занятию "7.2. Облачные провайдеры и синтаксис Terraform."
````yaml
terraform {
  required_providers {
    yandex = {
      source = "yandex-cloud/yandex"
    }
  }
  required_version = ">= 0.13"
}

provider "yandex" {
  token     = "AQAAAAA79qnSAATuwT0l4kEo-UCesD9-o3hSHuE"
  cloud_id  = "b1gvoc7aq6hmddfn86f4"
  folder_id = "b1g4761k63pdbhocj6h0"
  zone      = "ru-central1-a"
}

resource "yandex_compute_instance" "virt-1" {
  name = "netology-ter1"
  resources {
    cores  = 2
    memory = 2
  }
  boot_disk {
    initialize_params {
      image_id = "fd804nmi5gak42ae1dcq"
    }
  }
  network_interface {
    subnet_id = yandex_vpc_subnet.subnet-1.id
    nat       = true
  }
  metadata = {
    user-data = "${file("/home/vagrant/meta.txt")}"
    # ssh-keys = "debian:${file("~/.ssh/id_rsa.pub")}"
  }
}
resource "yandex_vpc_network" "network-1" {
  name = "network1"
}
resource "yandex_vpc_subnet" "subnet-1" {
  name           = "subnet1"
  zone           = "ru-central1-a"
  network_id     = yandex_vpc_network.network-1.id
  v4_cidr_blocks = ["192.168.2.0/24"]
}
output "internal_ip_address_virt_1" {
  value = yandex_compute_instance.virt-1.network_interface.0.ip_address
}
output "external_ip_address_virt_1" {
  value = yandex_compute_instance.virt-1.network_interface.0.nat_ip_address
}

````
