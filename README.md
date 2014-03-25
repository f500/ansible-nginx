Nginx
========

Install and start nginx
Removes the default server, and replaces it with a default 404 not-found server for every request.

Requirements
------------

Debian Wheezy with the package python-pycurl and python-software-properties installed.

Role Variables
--------------

All variables have sane defaults, but the following can be set:

    nginx_group: "www-data"
    nginx_php_force_cgi_redirect: false
    nginx_user: "www-data"
    nginx_worker_connections: 1024
    nginx_worker_processes: "{{ ansible_processor_count }}"
    nginx_www_dir: "/var/www"

    nginx_http_params:
        client_body_timeout: "10m"
        client_header_buffer_size: "1k"
        client_header_timeout: "10m"
        connection_pool_size: 256
        ignore_invalid_headers: "on"
        keepalive_timeout: "75 20"
        large_client_header_buffers: "4 2k"
        output_buffers: "1 32k"
        postpone_output: 1460
        request_pool_size: "4k"
        send_timeout: "10m"
        sendfile: "on"
        server_names_hash_bucket_size: 64
        tcp_nodelay: "on"
        tcp_nopush: "on"
        types_hash_max_size: 2048

The role also supports adding additional nginx servers, see the /defaults/main.yml file
for an example of how to add server(s). Default is an empty list:

    nginx_servers: []

Dependencies
------------

Depends on f500.repo_dotdeb.

Example Playbook
-------------------------

    - hosts: servers
      roles:
         - { role: f500.nginx }

License
-------

LGPL

Author Information
------------------

Jasper N. Brouwer, jasper@nerdsweide.nl

Ramon de la Fuente, ramon@delafuente.nl
