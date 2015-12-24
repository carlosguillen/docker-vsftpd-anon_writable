# docker-vsftpd-anon_writable

### Writable anonymous FTP server 

Runs a Docker image with vsftpd using anonymous access with writable folders. 
This is for testing BMS FTP only. 

***DO NOT USE IN PRODUCTION***

#### Get it, Build it, Run it
```bash
git clone git@github.com:carlosguillen/docker-vsftpd-anon_writable.git
cd docker-vsftpd-anon_writable
docker built -t docker-vsftpd-anon .
```

```
docker run --name "vsftpd" -d -p 20-21:20-21 -p 65500-65515:65500-65515 -v /some/path/pub:/var/ftp docker-vsftpd-anon
```

If using cunnard mode with BMS, create two folders CyberChargeIn and CyberPaxList inside /some/path/pub.
Manifest files using cunnard format can be placed inside the CyberPaxList folder.

#### Runtime Configuration Options (not needed for our testing)

There are a series of available variables you can tune at your own discretion. The defaults are most likely acceptable for most use cases.

* `ANON_ROOT` - The directory in the container which vsftpd will serve out (default: `/var/ftp`)
* `MAX_PORT` - The maximum port for pasv communiation (default: `65515`)
* `MIN_PORT` - The minimum port for pasv communication (default: `65500`)
* `MAX_PER_IP` - The maximum connections from one host (default: `2`)
* `MAX_LOGIN_FAILS` - Maximum number of login failures before kicking (default: `2`) 
* `MAX_CLIENTS` - Maximum number of simultaneously connected clients (default: `50`)
* `MAX_RATE` - Maximum bandwidth allowed per client in bytes/sec (default: `6250000`)
* `FTPD_BANNER` - An ftpd banner displayed when a client connects (default: `Welcome to an awesome public FTP Server`)

