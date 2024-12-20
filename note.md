Fri Dec 20 23:24:54 CST 2024

deploy yolo environment 

question:
ImportError: libGL.so.1: cannot open shared object file: No such file or directory
ImportError: libgthread-2.0.so.0: cannot open shared object file: No such file or directory

solve method:
linux system install the package named:libgl1、libglib2.0-0



---------------------------------------------------------------------
Sat Nov  2 10:42:24 AM CST 2024

check the process

command: 

ps aux  //check all the process  
//s stands for dormant  T stands for stop
---------------------------------------------------------------------
Fri Nov  1 15:18:03 AM CST 2024

learn machine learning,learn how to use a virtual environment to implement algorithms

use conda environment:

command: 

conda env list  、conda create -n m1_study python=3.8

pip list 、pip install numpy matplotlib

error:

ERROR: No matching distribution found for numpy

solve：

upgrade the veison of python

use command : conda update python
---------------------------------------------------------------------
Fri  1 Nov 11:02:30 CST 2024

check frp journalctl 

command: sudo journalctl -u frpc -f
---------------------------------------------------------------------
Fri Nov  1 10:33:35 AM CST 2024

how to check network connectivity

test id:

ping ip

test port:

telnet www.example.com 80
---------------------------------------------------------------------
Fri Nov  1 10:02:13 AM CST 2024

"openvpn_test" get server information 

know that openvpn start by systemctl

command:

sudo systemctl status openvpn@server

warning:

Consider setting groups/curves preference with tls-groups instead of forcing a specific cur>
Nov 01 00:07:13 VM-20-7-ubuntu ovpn-server\[649084\]: Note: Treating option '--ncp-ciphers' as  '--data-ciphers' (renamed in OpenVPN 2.5).

solves:

command：sudo nano /etc/openvpn/server.conf

ecdh-curve prime256v1 → tls-groups prime256v1

ncp-ciphers AES-128-GCM → data-ciphers AES-128-GCM

conmand: sudo nano systemctl restart openvpn@server

error:
---------------------------------------------------------------------
Fri Nov 01 10:17:46 2024 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Fri Nov 01 10:17:46 2024 TLS Error: TLS handshake failed