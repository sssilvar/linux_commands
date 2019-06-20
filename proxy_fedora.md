# Setup proxy in fedora
# DNF (change server)

Create a backup: ```sudo cp /etc/yum.repos.d/*.repo ~/Documents```

Then, execute: 
```
find /etc/yum.repos.d/ -maxdepth 1 -name "*.repo" -exec bash -c "sed -i 's/\&arch=\$basearch/\&arch=\$basearch\&country=US/' {}" \;
```

# Proxy for DNF
Append the following lines to `/etc/dnf/dnf.conf`:
```
proxy=http://proxyserver:port
proxy_username=username
proxy_password=your_password
```

## SSH
ProxyCommand /usr/bin/corkscrew proxy_server 8080 %h %p /home/ssilvari/.ssh/auth
ProxyCommand=socat - PROXY:proxy_server:%h:%p,proxyport=8080,proxyauth=username:password
