trellis-nginx-build
=========

An extension for trellis to allow nginx to be built from source enabling additional nginx modules like.

Requirements
------------

This is made specific to `trellis` so it obviously requires a trellis install, along with some basic understanding of it's setup. 


In your _requirements.yml_

    ## Build Nginx from source
    - name: trellis-nginx-build
      src: dylanlawrence.trellis-nginx-build
      version: 1.0.0

Run `ansible-galaxy install -r requirements.yml` to install the new role.

Role Variables
--------------

There are too many to list here, look in: _defaults/main.yml_

_TODO: Make variables accessable from group_vars_


Trellis Variables
--------------

A few changes need to happen in trellis files

_trellis/group_vars/*/main.yml_

Put `nginx_install_type=source` or `package` which also works to omit it from the roles as shown below. 

_trellis/roles/nginx/tasks/main.yml_

To avoid installing from package put `when: nginx_install_type == 'package'` on both `- name: Add Nginx PPA` and `- name: Install Nginx`

Playbook
----------------

_trellis/server.yml_
    
    ... before nginx role ...
    - { role: trellis-nginx-build, tags: [nginx], when: nginx_install_type == 'source' }
    - { role: nginx, tags: [nginx] }


Nginx Includes | Wordpress Sites *.conf
--------------------

If you add a directory like (below) with any named file like *.conf.j2
you can add module specific config. 

_trellis/nginx-includes/[yoursite.com]/pagespeed.conf.j2_

    pagespeed on;
    pagespeed FileCachePath /var/ngx_pagespeed_cache;
    pagespeed EnableFilters lazyload_images;


Dependencies
------------

xenial only so far

License
-------

BSD

Author Information
------------------

Dylan Lawrence


