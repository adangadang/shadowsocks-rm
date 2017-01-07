shadowsocks-rm manyuser for shadowsocks-panel
----------------

Install
-------

Debian / Ubuntu:

    apt-get install python-pip python-m2crypto

CentOS:

    yum install m2crypto python-setuptools
    easy_install pip

install MySQL 5.x.x

`pip install cymysql`


edit config.py

Example:

    import logging
    
    #Config
    MYSQL_HOST = 'localhost'
    MYSQL_PORT = 3306
    MYSQL_USER = 'root'
    MYSQL_PASS = 'password'
    MYSQL_DB = 'shadowsocks'
    
    # Pro node 1 true , others false
    PRO_NODE = 0
    
    MANAGE_PASS = 'passwd'
    #if you want manage in other server you should set this value to global ip
    MANAGE_BIND_IP = '127.0.0.1'
    #make sure this port is idle
    MANAGE_PORT = 23333
    #BIND IP
    #if you want bind ipv4 and ipv6 '[::]'
    #if you want bind all of ipv4 if '0.0.0.0'
    #if you want bind all of if only '4.4.4.4'
    SS_BIND_IP = '0.0.0.0'
    SS_METHOD = 'rc4-md5'
    
    #LOG CONFIG
    LOG_ENABLE = False
    LOG_LEVEL = logging.DEBUG
    LOG_FILE = '/var/log/shadowsocks.log'


TestRun `cd shadowsocks` ` python servers.py` not server.py
#python server.py -k password  -d start
if no exception server will startup. you will see such like
Example:

    add: {"server_port": XXXXX, "password":"XXXXX", "method":"xxxxx"}


Database user table column
------------------
`sspwd` server pass

`port` server port

`lastConnTime` last keepalive time

`flow_up` upload transfer

`flow_down` download transfer (upload & download in here now)

`transfer` if flow_up + flow_down > transfer this server will be stop (db_transfer.py del_server_out_of_bound_safe)

