# Ansible Role: Install Flatpak and add Flathub repo

[![License][license-image]][license-url] [![Ansible Galaxy][ansible-galaxy-image]][ansible-galaxy-url] [![CircleCI][circleci-image]][circleci-url]

Install [Flatpak](https://flatpak.org/) for Linux.

## Work on

```yaml
  platforms:
    - name: Fedora
      versions:
        - 32
        - 31
        - 30
    - name: Ubuntu
      versions:
        - eoan
        - disco
        - cosmic
        - bionic
        - xenial
        - trusty
    - name: Debian
      version:
        - jessie
        - stretch
        - buster
        - stable
        - testing
    - name: EL (CentOS)
      versions:
        - 8
        - 7
    - name: opensuse
      vesrion:
        - tumbleweed
    - name: ArchLinux
      version:
        - any
```

## Requirements

[min_ansible_version: 2.6](https://docs.ansible.com/ansible/latest/modules/flatpak_module.html)

## Role Variables

None.

## Dependencies

None.

## Example Playbook

`install-firefox-over-flatpak.yml`:

```yaml
- name: Install FireFox
  hosts: all
  strategy: free
  serial:
    - "100%"
  roles:
    - ansible-role-install-flatpak
  tasks:

    - name: Install FF over flatpak
      become: yes
      flatpak:
        name: https://flathub.org/repo/appstream/org.mozilla.firefox.flatpakref
        method: system
        state: present
      tags:
        - firefox
        - flatpak
```

## License

Apache License, Version 2.0

## Author Information

[don Rumata](https://github.com/don-rumata)

## TODO

- ~~Add tests.~~
- Add more tests.

[license-image]: https://img.shields.io/github/license/don-rumata/ansible-role-install-flatpak.svg
[license-url]: https://opensource.org/licenses/Apache-2.0

[ansible-galaxy-image]: https://img.shields.io/badge/ansible_galaxy-don__rumata.ansible__role__install__flatpak-blue.svg
[ansible-galaxy-url]: https://galaxy.ansible.com/don_rumata/ansible_role_install_flatpak

[circleci-image]: https://circleci.com/gh/don-rumata/ansible-role-install-flatpak.svg?style=shield
[circleci-url]: https://circleci.com/gh/don-rumata/ansible-role-install-flatpak
