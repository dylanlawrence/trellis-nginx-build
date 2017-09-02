trellis-nginx-build role
=========

An extension for trellis to allow nginx to be built from source enabling additional nginx modules like .

Requirements
------------

This is made specific to `trellis` so it obviously requires a trellis install, along with some basic understanding of it's setup. 


In your _requirements.yml_

    ## Build Nginx from source
    - name: trellis-nginx-build
      src: dylanlawrence.trellis-nginx-build
      version: 0.0.1

TODO : New to this galaxy so not sure about ^ yet?
_(pun intented)_

Role Variables
--------------

There are too many to list here, look in: 

_defaults/main.yml_


Dependencies
------------



Playbook Changes to trellis
----------------

_server.yml_
    - { role: nginx-build, tags: [nginx], when: nginx_install_type == 'source' }
    - { role: nginx, tags: [nginx] }

License
-------

BSD

Author Information
------------------

Dylan Lawrence


