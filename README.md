Elasticsearch Curator
=========

An Ansible role for installing the Elasticsearch curator in a Ubuntu machine

Requirements
------------

None

Role Variables
--------------

You can configure the path for the configuration files with this var:
```
config_path: /etc/curator
```

If you need to authenticate the requests when using AWS ES service you should enable this variable:
```
enable_aws_es: false
```

The client configuration file is defined as per the YAML config file described in Curator [docs](http://www.elastic.co/guide/en/elasticsearch/client/curator/current/configfile.html)

```
client:
  hosts: ['localhost']
  port: 9200
  url_prefix:
  use_ssl: false
  certificate:
  client_cert:
  client_key:
  ssl_no_validate: false
  http_auth:
  timeout: 30
  master_only: false

logging:
  loglevel: INFO
  logfile: /var/log/curator.log
  logformat: json
  blacklist: ['elasticsearch', 'urllib3']
```

The actions configuration file is defined as per the YAML config file described in Curator [docs](http://www.elastic.co/guide/en/elasticsearch/client/curator/current/actionfile.html)

```
actions: []
```


Dependencies
------------

None

Example Playbook
----------------
```
- hosts: all
  roles:
    - role: jobscore.curator
      actions: []
      client:
        hosts: ['localhost']
        port: 9200
      logging:
        loglevel: INFO
        logfile: /var/log/curator.log
        logformat: json
        blacklist: ['elasticsearch', 'urllib3']
```
License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a
website (HTML is not allowed).
