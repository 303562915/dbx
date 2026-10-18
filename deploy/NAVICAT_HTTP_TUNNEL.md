# Navicat MySQL HTTP Tunnel

DBX supports Navicat's MySQL HTTP tunnel protocol. A compatibility copy of
PremiumSoft's `ntunnel_mysql.php` is in `deploy/navicat/dbx_tunnel.php`.
Navicat documents that its original script is supplied in its installation
folder/package on Windows and can be exported from the HTTP tab on macOS and
Linux:
https://help.navicat.com/hc/en-us/articles/218283457-Where-can-I-get-the-HTTP-tunnel-script-file

The script is proprietary and its use and redistribution are subject to the
applicable Navicat EULA. Review those terms before copying or deploying it:
https://www.navicat.com/manual/pdf_manual/en/navicat_17/win_manual/navicat_en.pdf
The script header includes these source and license references. DBX does not
grant rights to the PremiumSoft code.

The separate `deploy/dbx_tunnel.php` file is DBX's own tunnel and is not a
Navicat-compatible endpoint.

Upload `deploy/navicat/dbx_tunnel.php` to the PHP host and configure DBX with
its full URL, such as `https://db.example.com/dbx_tunnel.php`. Plain HTTP is accepted for trusted
private networks, but it exposes database credentials and SQL in transit. If
the endpoint redirects HTTP to HTTPS, configure DBX with the final HTTPS URL;
redirects are not followed because they can change a POST request into a GET.

This protocol supports regular queries, `USE`, ping, and disconnect. MySQL TLS
and prepared statements are not supported by the Navicat HTTP tunnel protocol.
