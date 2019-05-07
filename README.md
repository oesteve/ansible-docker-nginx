Role Name
=========

Nginx in a Docker With Let's Encrypt certs generation

Requirements
------------

This role require Ubuntu and Docker

Role Variables
--------------

    services_dir: /opt  # Root dir for container data
    
    docker_image: nginx # Docker nginx image
    docker_name: nginx  # Docker nginx container name
    
    lets_encrypt_rsa_key_size: 2048    # Let's Encrypt rsa key size
    lets_encrypt_account_email: false  # Let's Encrypt  account email (optional)
    
    generate_certs: false # Do you want generate/refresh certs ?
    
    backends: []          # Backends config

Dependencies
------------

N/A

Example Playbook
----------------

A simple example

    ---
    - name: Install Nginx Http 2.0 with Let's Encrypt
      hosts: servers
      vars:
        backends:
          - name: oscaresteve.com
            hostnames:
              - oscaresteve.com
              - www.oscaresteve.com
            servers:
              - 172.17.0.1:8088
      roles:
        - ansible-docker-nginx

Generate certs as optional var

    ansible-playbook -i inventory/hosts.ini install-nginx.yml --extra-vars "generate_certs=True"

License
-------

BSD

Author Information
------------------

Óscar Esteve - http://oscaresteve.com
