Role Name
=========

The role with which you can install a fully ready-to-work PrestaShop.
Just complete variables (vars/main.yml) and your host (hosts.ini)

Requirements
------------

There are no requirements. Everything you need is included role :)

Role Variables
--------------

Link to latest PrestaShop.

    prestashop_url: 'https://github.com/PrestaShop/PrestaShop/releases/download/1.7.7.2/prestashop_1.7.7.2.zip'

Defines whether you want to install MySQL or not. If True ansible will install MySQL else not.

    mysql_install: True

Credentials to your MySQL.

    mysql_host: 'localhost'
    mysql_user: 'root'
    mysql_user_password: 'rootpwd'

Credentials for MySQL user which will use database.

    mysql_prestashop_user: 'prestashopuser'
    mysql_prestashop_password: 'prestashoppwd'

Name of database for PrestaShop

    mysql_prestashop_db: 'prestashop'

Dependencies
------------

You don't need any dependencies.

Example Playbook
----------------

Example playbook is in root directory of repo.

    ---
    - name: Prestashop deploy
      hosts: MyServer
      become: true
      become_user: root
      roles:
        - role: common
        - role: php
        - role: mysql
        - role: apache
        - role: prestashop

You can run playbook like that:
sudo ansible-playbook -i hosts.ini --ask-pass prestashop-deploy.yml

Troubleshooting
-------
1. Non-local MySQL:
If you want use MySQL on other server, you should delete from mysql.yml all of `login_unix_socket: /var/run/mysqld/mysqld.sock`

License
-------

MIT

Author Information
------------------

The role was created in 2021 by Bartłomiej Komendarczuk
