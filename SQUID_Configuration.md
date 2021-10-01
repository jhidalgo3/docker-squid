# Squid: forward to another proxy (with authentication details for the parent proxy)

[Squid configuration directive cache_peer](http://www.squid-cache.org/Doc/config/cache_peer/)

```
http_access allow all
http_port 3128

coredump_dir /var/spool/squid3
refresh_pattern ^ftp:       1440    20% 10080
refresh_pattern ^gopher:    1440    0%  1440
refresh_pattern -i (/cgi-bin/|\?) 0 0%  0
refresh_pattern (Release|Packages(.gz)*)$      0       20%     2880
refresh_pattern .       0   20% 4320

cache_peer 10.1.2.3 parent 80 0 no-query default login=my_username:my_password
never_direct allow all
```
