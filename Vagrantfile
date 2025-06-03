# -*- mode: ruby -*-
# vi: set ft=ruby :
#
# Vagrant configuration file
#
# References:
#
# * Vagrantfile | Vagrant | HashiCorp Developer
#   https://developer.hashicorp.com/vagrant/docs/vagrantfile
#
# Copyright 2025 林博仁(Buo-ren Lin) <buo.ren.lin@gmail.com>
# SPDX-License-Identifier: CC-BY-SA-4.0+ OR LicenseRef-Apache-2.0-If-Not-Used-In-Template-Projects

Vagrant.configure("2") do |config|
  # Get the directory name containing this Vagrantfile to use as VM name prefix
  project_name = File.basename(Dir.pwd)

  # Find more Vagrant boxes at:
  # https://portal.cloud.hashicorp.com/vagrant/discover?architectures=amd64&providers=virtualbox&query=bento
  config.vm.box = "bento/ubuntu-24.04"
  #config.vm.box = "bento/debian-12"
  #config.vm.box = "bento/fedora-41"
  #config.vm.box = "bento/rockylinux-9"

  # Configure synced folders for ease access to project files
  config.vm.synced_folder ".", "/vagrant"

  config.vm.provider :virtualbox do |v|
    v.cpus = 2
    v.memory = 512

    # Use Virt-IO network adapter to improve networking performance
    v.default_nic_type = "virtio"
  end

  config.vm.define "app" do |app|
    app.vm.hostname = "app"
    app.vm.provider :virtualbox do |v|
      v.name = "#{project_name} - Application server"
    end
  end

  config.vm.define "db" do |db|
    db.vm.hostname = "db"
    db.vm.provider :virtualbox do |v|
      v.name = "#{project_name} - Database server"
    end
  end
end
