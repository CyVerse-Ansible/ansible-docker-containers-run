CyVerse Ansible Docker Containers Run
===================

This role will define and run a given set of docker containers

Requirements
------------

This role assumes you have docker installed.

Role Variables
--------------

The following table lists optional ansible variables along with the default values if not defined.

Variable Name | Default value if not defined | Description
------------- | ---------------------- | -----------
DOCKER_IMAGES | None | a dictionary of docker image vars containing the image, tag, name, ports, and volumes.
DOCKER_IMAGE  | None | part of DOCKER_IMAGES; the docker image used
DOCKER_IMAGE_TAG | None | part of DOCKER_IMAGES; the docker containers tag
DOCKER_IMAGE_NAME  | None | part of DOCKER_IMAGES; the docker containers name
DOCKER_PORTS  | None | part of DOCKER_IMAGES; the ports maped to the docker image. Use [] to leave blank
DOCKER_VOLUMES  | None | part of DOCKER_IMAGES; the volumes attached to the docker image. Use [] to leave blank

Example Playbook
----------------

This is a sample playbook:
````
- hosts: all
  become: true
  roles:
    - ansible-docker-containers-run
  vars:
    DOCKER_IMAGES:
      - DOCKER_IMAGE: "ubuntu:18.04"
        DOCKER_IMAGE_TAG: "ubuntutest18"
        DOCKER_IMAGE_NAME: "ryan_test18"
        DOCKER_PORTS: ["8080:9001"]
        DOCKER_VOLUMES: ["/tmp:/tmp"]
      - DOCKER_IMAGE: "ubuntu:20.04"
        DOCKER_IMAGE_TAG: "ubuntutest20"
        DOCKER_IMAGE_NAME: "ryan_test20"
        DOCKER_PORTS: [""]
        DOCKER_VOLUMES: [""]
````

Author Information
------------------
Ryan Schneider (rschneider@cyverse.org)
