root@103725795523314:~# ufw default deny incoming
Default incoming policy changed to 'deny'
(be sure to update your rules accordingly)
root@103725795523314:~# ufw default allow outgoing
Default outgoing policy changed to 'allow'
(be sure to update your rules accordingly)
root@103725795523314:~# ufw allow 22/tcp
Skipping adding existing rule
Skipping adding existing rule (v6)
root@103725795523314:~# ufw allow 8080/tcp
Skipping adding existing rule
Skipping adding existing rule (v6)
root@103725795523314:~# ufw enable
Command may disrupt existing ssh connections. Proceed with operation (y|n)? y
Firewall is active and enabled on system startup
root@103725795523314:~# ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
80/tcp                     ALLOW IN    Anywhere
443/tcp                    ALLOW IN    Anywhere
22/tcp                     ALLOW IN    Anywhere
8080/tcp                   ALLOW IN    Anywhere
3306/tcp                   ALLOW IN    Anywhere
22/tcp (OpenSSH)           ALLOW IN    Anywhere
80,443/tcp (Nginx Full)    ALLOW IN    Anywhere
8081/tcp                   ALLOW IN    Anywhere
8082/tcp                   ALLOW IN    Anywhere
80/tcp (v6)                ALLOW IN    Anywhere (v6)
443/tcp (v6)               ALLOW IN    Anywhere (v6)
22/tcp (v6)                ALLOW IN    Anywhere (v6)
8080/tcp (v6)              ALLOW IN    Anywhere (v6)
3306/tcp (v6)              ALLOW IN    Anywhere (v6)
22/tcp (OpenSSH (v6))      ALLOW IN    Anywhere (v6)
80,443/tcp (Nginx Full (v6)) ALLOW IN    Anywhere (v6)
8081/tcp (v6)              ALLOW IN    Anywhere (v6)
8082/tcp (v6)              ALLOW IN    Anywhere (v6)

root@103725795523314:~# ss -tlnp
State       Recv-Q      Send-Q           Local Address:Port              Peer Address:Port      Process
LISTEN      0           151                  127.0.0.1:3306                   0.0.0.0:*          users:(("mysqld",pid=156262,fd=23))
LISTEN      0           511                    0.0.0.0:8081                   0.0.0.0:*          users:(("nginx",pid=218462,fd=5),("nginx",pid=218461,fd=5),("nginx",pid=218460,fd=5))
LISTEN      0           511                    0.0.0.0:8082                   0.0.0.0:*          users:(("nginx",pid=218462,fd=6),("nginx",pid=218461,fd=6),("nginx",pid=218460,fd=6))
LISTEN      0           4096                127.0.0.54:53                     0.0.0.0:*          users:(("systemd-resolve",pid=102568,fd=17))
LISTEN      0           70                   127.0.0.1:33060                  0.0.0.0:*          users:(("mysqld",pid=156262,fd=21))
LISTEN      0           4096                   0.0.0.0:22                     0.0.0.0:*          users:(("sshd",pid=108551,fd=3),("systemd",pid=1,fd=217))
LISTEN      0           511                    0.0.0.0:80                     0.0.0.0:*          users:(("nginx",pid=218462,fd=7),("nginx",pid=218461,fd=7),("nginx",pid=218460,fd=7))
LISTEN      0           4096             127.0.0.53%lo:53                     0.0.0.0:*          users:(("systemd-resolve",pid=102568,fd=15))
LISTEN      0           4096                      [::]:22                        [::]:*          users:(("sshd",pid=108551,fd=4),("systemd",pid=1,fd=218))
LISTEN      0           511                       [::]:80                        [::]:*          users:(("nginx",pid=218462,fd=8),("nginx",pid=218461,fd=8),("nginx",pid=218460,fd=8))
root@103725795523314:~#
