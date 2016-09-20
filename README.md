# avahi service definitions #

## avahi defaults ##
The avahi package includes 2 service definitions "out-of-the-box":
- ssh.service
- sftp-ssh.service

## our additional definitions ##
So far, we've added avahi ".service" (definition) files for the following services:
- _domain.service:_
	- **\_domain.\_udp**
	- PORT **53**
	- Domain Name Service server
- _epmd-tcp.service:_
	- **\_epmd.\_tcp**
	- PORT **4369**
	- Erlang Port Mapper daemon
- _epmd-udp.service:_
	- **\_epmd.\_udp**
	- PORT **4369**
	- Erlang Port Mapper daemon
- _kpasswd5-tcp.service:_
	- **\_kpasswd5.\_tcp**
	- PORT **464**
	- Kerberos Password daemon
- _kpasswd5-udp.service:_
	- **\_kpasswd5.\_udp**
	- PORT **464**
	- Kerberos Password daemon
- _ldap-tcp.service:_
	- **\_ldap.\_tcp**
	- PORT **389**
	- LDAP server
- _ldap-udp.service:_
	- **\_ldap.\_udp**
	- PORT **389**
	- LDAP server
- _memcached-tcp.service:_
	- **\_memcached.\_tcp**
	- PORT **11211**
	- memcache daemon
- _memcached-udp.service:_
	- **\_memcached.\_udp**
	- PORT **11211**
	- memcache daemon
- _ntp.service:_
	- **\_ntp.\_udp**
	- PORT **123**
	- Network Time Protocol server
- _samba.service:_
	- **\_smb.\_tcp**
	- PORT **139**
	- Server Message Block daemon
- _sunrpc-tcp.service:_
	- **\_sunrpc.\_tcp**
	- PORT **111**
	- SUN RPC Port Mapper daemon
- _sunrpc-udp.service:_
	- **\_sunrpc.\_udp**
	- PORT **111**
	- SUN RPC Port Mapper daemon

## INSTALLATION ##
Obviously, installation procedure will differ by the distribution of Linux/UNIX running on your
box. We will try to provide details for as many distributions as possible, however, some of this
may rely on a volunteer effort.

### FreeBSD 10.3 ###
With the **avahi** package installed from the **FreeBSD Ports Collection**, it's a straightforward
process _(I'd assume the **pkg** is the same)_; it's as simple as copying the *.service files
to their new home:

	/usr/local/etc/avahi/services/

Ensure that the **avahi_daemon** service is enabled:

	# sysrc avahi_daemon_enable="YES"

And restart it _(unfortunately, it does not have a **restart** command, so we can use **stop** and **start** to acheive the same result)_:

	# service avahi-daemon stop
	# sleep 5
	# service avahi-daemon start

The presence of the newly-advertised services can be verified with **avahi-browse**:

	# avahi-browse --all --verbose

