Configuration RTP Ports
Docker doesn't currently allow a range of ports to be opened, as such all RTP ports have to be specified on the command line. In the example above we are only opening 10, so you will be limited to 10 simulataneous calls.

Edit the Asterisk RTP configuration to ensure only these ports are used.

Edit /etc/asterisk/rtp.conf:

rtpstart=16384
rtpend=16394

Or:

$ sed -i "s/rtpstart=10000/rtpstart=16384/g" /etc/asterisk/rtp.conf
$ sed -i "s/rtpend=20000/rtpend=16394/g" /etc/asterisk/rtp.conf


Now, you can launch a new container and open ports for your container mydebianapacheasterisk:

$ docker run -d -p 9080:80 -p 5060:5060/tcp -p 5060:5060/udp -p 16384:16384/udp -p 16385:16385/udp -p 16386:16386/udp -p 16387:16387/udp -p 16388:16388/udp -p 16389:16389/udp -p 16390:16390/udp -p 16391:16391/udp -p 16392:16392/udp -p 16393:16393/udp -p 16394:16394/udp mydebian_apache_asterisk run
You can start as many containers as you want and stop them with docker stop. The command docker ps will allow you to watch all the running containers and the ports mapped to them.



