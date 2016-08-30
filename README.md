ansible-nginxauthdaemon
=========

Role for installing Python daemon for authentificaton (<https://pypi.python.org/pypi/nginxauthdaemon>)

Requirements
------------

Any host with python and systemd should fit.

Role Variables
--------------

Basic configuration properties are:

* `nginxauth_realm` - Realm name shown on login page, default `Example`
* `nginxauth_version` - pypi package version, default `1.0.0a2`
* `nginxauth_user` - user for daemon launching, default `nginxauth`
* `nginxauth_home` - installation directory, default `/opt/nginxauth`
* `nginxauth_listen_ip` - gunicorn listen ip:port, default `127.0.0.1:5000`
* `nginxauth_session_salt` - long string used a salt for creation of session key.
* `nginxauth_des_iv` - 8byte initial vector for DES algorithm
* `nginxauth_des_key` - 8byte DES encryption key
* `nginxauth_authentificator` - authenticator class name, by default `nginxauthdaemon.auth.DummyAuthenticator`. Authenticators available out-of-the-box:
	* `nginxauthdaemon.auth.DummyAuthenticator` - Simplest authenticator checking username equals password
	* `nginxauthdaemon.crowdauth.CrowdAuthenticator` - Atlassian Crowd based authenticator

Crowd authenticator has additional options:

* `nginxauth_crowd_url` - Crowd server URL, for ex http://localhost:8095/crowd/
* `nginxauth_crowd_name` - Crowd application name
* `nginxauth_crowd_pass` - Crowd application password


Example Playbook
----------------
```
- hosts: prometheus
  name: prometheus
  roles:
    - role: unitedtraders.nginxauthdaemon
```

Additional information
-------
After setup, daemon listen on http://127.0.0.1:5000 for incoming connections. Do not forget to setup your Nginx as described here: <https://pypi.python.org/pypi/nginxauthdaemon>

License
-------

BSD

Author Information
------------------

Anton Markelov <doublic@gmail.com> - <https://github.com/strangeman>