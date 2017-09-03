
NOT WORKING YET - In hopes of lifting this `galaxy role` idea I have a started this process by moving the code over that I have working in a folder in a trellis env. 

trellis-nginx-build role
=========

An extension for trellis to allow nginx to be built from source enabling additional nginx modules like.

Requirements
------------

This is made specific to `trellis` so it obviously requires a trellis install, along with some basic understanding of it's setup. 


In your _requirements.yml_

    ## Build Nginx from source
    - name: trellis-nginx-build
      src: dylanlawrence.trellis-nginx-build
      version: 0.1.0

TODO : New to this galaxy so not sure about ^ yet?
_(pun intented)_

Run `ansible-galaxy install -r requirements.yml` to install the new role.


Role Variables
--------------

There are too many to list here, look in: 

_defaults/main.yml_

Also required a way to turn off the standard package install part of the trellis nginx role.

I went with `nginx_install_type=source` in the _all/main.yml_ which also works to omit it from the roles as shown below. 

Playbook Changes to trellis
----------------

_server.yml_
    
    ... before nginx role ...
    - { role: nginx-build, tags: [nginx], when: nginx_install_type == 'source' }
    - { role: nginx, tags: [nginx] }


Dependencies
------------

N/A

License
-------

BSD

Author Information
------------------

Dylan Lawrence


