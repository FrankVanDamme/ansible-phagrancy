# Phagrancy Docker Ansible role.

This role will install Phagrancy, running it in two Docker containers (nginx and php-fpm). Phagrancy is a self hosted reposiroty for Vagrant boxes and allows to store vagrant boxes and use the repository from within a Vagrantfile.

You will need to prepare a space to put your Vagrant boxes (directory, partition) and a TLS certificate key pair (put it in a directory "certs"). 

A playbook like this will work:

```
---

- hosts: yourdockerhost
  gather_facts: no
  roles:
      - phagrancy
  vars:
      builddir: "phagrancy-build"
      server_name: vagrantrepo.yourdomain.com
      access_token: abcdefgh
      api_token: 12345678
      access_password: qwertyui
```

Run the playbook:

```
you@yourworkstation:~$ ansible-playbook --ask-become-pass phagrancy-install.yml -i inventory.ini
```



# References

* Official Phagrancy Github project page: https://github.com/dlundgren/phagrancy/ (see Wiki and the README in the "docker" subdirectory)
