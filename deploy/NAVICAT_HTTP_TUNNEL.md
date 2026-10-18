# Navicat MySQL HTTP Tunnel

DBX supports Navicat's MySQL HTTP tunnel protocol, but does not redistribute
the PremiumSoft `ntunnel_mysql.php` script. Navicat documents that the script
is supplied in its installation folder/package on Windows and can be exported
from the HTTP tab on macOS and Linux. Obtain it from an authorized Navicat
distribution and deploy it on a PHP host that can reach the MySQL server:
https://help.navicat.com/hc/en-us/articles/218283457-Where-can-I-get-the-HTTP-tunnel-script-file

The Navicat EULA restricts copying and distribution of the software except as
expressly allowed by that agreement. DBX therefore does not include a modified
copy of the proprietary script. Review the terms that apply to your Navicat
edition before copying or deploying it:
https://www.navicat.com/manual/pdf_manual/en/navicat_17/win_manual/navicat_en.pdf

The separate `deploy/dbx_tunnel.php` file is DBX's own tunnel and is not a
Navicat-compatible endpoint.

Configure the connection URL with the full script URL, such as
`https://db.example.com/ntunnel_mysql.php`. Plain HTTP is accepted for trusted
private networks, but it exposes database credentials and SQL in transit. If
the endpoint redirects HTTP to HTTPS, configure DBX with the final HTTPS URL;
redirects are not followed because they can change a POST request into a GET.

This protocol supports regular queries, `USE`, ping, and disconnect. MySQL TLS
and prepared statements are not supported by the Navicat HTTP tunnel protocol.
