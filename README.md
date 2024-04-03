# Ansible Role Klipper

Library of Ansible plugins and roles for deploying various services.
See [ansible-roles](https://github.com/davidfischer-ch/ansible-roles) for additional documentation.

This repository hosts the role Klipper and may depend of other roles and plugins of the library.

## Disclaimer

I wish I could run Klipper on Docker... But...

1. It seem we have to install Octoprint head-to-head with it.
2. It seem we have to mess with https://github.com/dimalo/klipper-web-control-docker/issues/51
3. There is no official image, maybe this [attempt](https://github.com/dimalo/klipper-web-control-docker)?

This is a nogo for my current setup (OctoPi).

So I wrote this Ansible Role to replace the *installation script* and setup Klipper on a Raspberry Pi 4 dedicated to manage my printer (Zero G Mercury One.1).

Sometimes old school DevOps is the way to go.

## Dependencies

See [meta](meta/main.yml).

## Variables

TODO VARIABLES

## Example

A complete example (stack) will be made available when I used it for some time.

Example for installing Klipper on your OctoPi.

### Playbook

```
---

- hosts:
    - myprinter_raspberrypi
  roles:
    - klipper
  vars:
    user: '{{ ansible_user }}'

    python_packages:
      - python3-dev
      - python3.9
      - python3.9-dev
      - python3.9-minimal
    python_versions: ['3.9']
    python_pypy_versions: []
    python_build_install_dependencies_of: python3

    # https://github.com/Klipper3d/klipper/commits
    klipper_version: 75a40e817db4d5bc9d7d893fad499907d2b910a2
    klipper_python_executable: python3.9 # Yes not 2.7, even 3.9 is outdated :(
```

## License

See [LICENSE.rst](LICENSE.rst).

## Authors

See [AUTHORS](AUTHORS).

2014-2024 - David Fischer
