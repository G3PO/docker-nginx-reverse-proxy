# docker-nginx-reverse-proxy
Docker image for a reverse proxy, powered by nginx.

##Build

To create the image `lerenn/nginx-reverse-proxy`, execute the following command on the openvpn-server project folder:

    docker build -t lerenn/nginx-reverse-proxy .

##Run

To run the image with a minimum of arguments, execute the following command :

    docker run -d lerenn/nginx-reverse-proxy

However, if you want to use a reverse-proxy on HTTP only websites :

    docker run -d -p 80:80 -v /path/in/host:/etc/nginx/sites-enabled lerenn/nginx-reverse-proxy

And if you want to use a reverse-proxy on HTTP and/or HTTPS websites :

    docker run -d -p 80:80 -p 443:443 -v /path/in/host:/etc/nginx/sites-enabled -v /path/in/host:/etc/nginx/certificates lerenn/nginx-reverse-proxy

##Arguments

###Volumes

#### Server files

The server files and configuration are placed in the volume `/etc/openvpn`. To persist server files and configuration, add this argument to the launch command : `-v /path/in/host:/etc/openvpn`
If the server directory is empty, a new server will be created. Otherwise, the old one will be used.

### Ports

* **80**: HTTP port.
* **443**: HTTPS port.
