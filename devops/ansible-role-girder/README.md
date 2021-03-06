girderformindlogger.girderformindlogger
=============
[![Apache 2.0](https://img.shields.io/badge/license-Apache%202-blue.svg)](https://raw.githubusercontent.com/girderformindlogger/ansible-role-girderformindlogger/master/LICENSE)
[![Build Status](https://travis-ci.org/girderformindlogger/ansible-role-girderformindlogger.svg?branch=master)](https://travis-ci.org/girderformindlogger/ansible-role-girderformindlogger)

An Ansible role to install [Girder](https://github.com/girderformindlogger/girderformindlogger).

Further documentation on provisioning can be found [here](https://girderformindlogger.readthedocs.io/en/latest/provisioning.html).

Requirements
------------

Ubuntu 16.04+.

Role Variables
--------------

| parameter               | required | default                                    | comments                                                                                                 |
| ----------------------- | -------- | ------------------------------------------ | -------------------------------------------------------------------------------------------------------- |
| girder_bind_public      | no       | false                                      | Whether to bind to all network interfaces.                                                               |
| girder_daemonize        | no       | true                                       | Whether to install the systemd service.                                                                  |
| girder_database_uri     | no       | mongodb://localhost:27017/girderformindlogger           | The Connection String URI for MongoDB.                                                                   |
| girder_development_mode | no       | false                                      | Whether to enable Girder's development mode and disable HTTP reverse proxy configuration.                |
| girder_package          | no       | girderformindlogger                                     | Package name to install via ``pip``, can be a path.                                                      |
| girder_pip_extra_args   | no       |                                            | Any extra arguments to pass to ``pip`` when installing girderformindlogger.                                           |
| girder_version          | no       |                                            | PyPI version of Girder to install.                                                                       |
| girder_virtualenv       | no       | {{ ansible_user_dir }}/.virtualenvs/girderformindlogger | Path to a Python virtual environment to install Girder in. Will be implicitly created if using Python 3. |
| girder_web              | no       | true                                       | Whether to build the Girder web client.                                                                  |
