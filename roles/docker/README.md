Docker
=========

Install Docker on Linux

Supported OS:

* [x] Debian/Ubuntu
* [x] RedHat/CentOS

Requirements
------------

Don't have any requirements

Role Variables
--------------

Docker Edition

* docker_edition: 'ce'
* docker_package: "docker-{{ docker_edition }}"
* docker_package_state: present

Service Options

* docker_service_state: started
* docker_service_enabled: true

Docker Compose options.

* docker_install_compose: true
* docker_compose_version: "1.24.1"
* docker_compose_path: /usr/local/bin/docker-compose

Used only for Debian/Ubuntu. Switch 'stable' to 'edge' if needed.

* docker_apt_release_channel: stable
* docker_apt_arch: amd64
* docker_apt_repository: "deb [arch={{ docker_apt_arch }}] https://download.docker.com/linux/{{ ansible_distribution|lower }} {{ ansible_distribution_release }} {{ docker_apt_release_channel }}"
* docker_apt_ignore_key_error: true

Used only for RedHat/CentOS/Fedora.

* docker_yum_repo_url: https://download.docker.com/linux/{{ (ansible_distribution == "Fedora") | ternary("fedora","centos") }}/docker-{{ docker_edition }}.repo
* docker_yum_repo_enable_edge: 0
* docker_yum_repo_enable_test: 0

Dependencies
------------

None

Example Playbook
----------------

Edit in target.yml

    - hosts: someGroups
      roles:
         - consul
