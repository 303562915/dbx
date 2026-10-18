# Navicat MySQL HTTP Tunnel

DBX supports Navicat's MySQL HTTP tunnel protocol, but does not redistribute
the PremiumSoft `ntunnel_mysql.php` script. Obtain that script from a Navicat
distribution you are authorized to use and deploy it on a PHP host that can
reach the MySQL server.

Configure the connection URL with the full script URL, such as
`https://db.example.com/ntunnel_mysql.php`. Plain HTTP is accepted for trusted
private networks, but it exposes database credentials and SQL in transit. If
the endpoint redirects HTTP to HTTPS, configure DBX with the final HTTPS URL;
redirects are not followed because they can change a POST request into a GET.

This protocol supports regular queries, `USE`, ping, and disconnect. MySQL TLS
and prepared statements are not supported by the Navicat HTTP tunnel protocol.
