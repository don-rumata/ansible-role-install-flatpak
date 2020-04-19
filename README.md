Ansible Role: Install Flatpak and add Flathub repo
===================================================

Install [Flatpak](https://flatpak.org/) for Linux.

Requirements
------------

None.

Role Variables
--------------

None.

Dependencies
------------

None.

Example Playbook
----------------

install-firefox-over-flatpak.yml
```yml
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


License
-------

Apache License, Version 2.0

Author Information
------------------

[don Rumata](https://github.com/don-rumata)

TODO
----
  - Add support OpenSUSE.
  - Add tests.
