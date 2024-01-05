# Wireguard-Bypass_CGNAT
For certain region or country, local ISP are managing your home network using CGNAT(Carrier-grade NAT), which prevents you from doing port-forwarding on your router and expose your home server externally. After some research, I found that it is more expensive to host your server on the cloud(based on your CPU and memory requirements), so I made this guide to provide a lower-cost option for those who wants to expose their home lab or infrastructure out.

There are great solutions out there, such as Cloudflare Tunnel, which make it possible for you to expose your home lab without port-forwarding. Still, there is a limitation in terms of the protocol allowed to expose, as well as the limitation to run media streaming.

My solution here is to provide a basic setup using open-source solution call wireguard and with the help of a cheap, low-cost VPS, or a server that has a public IP, to serve as the main gateway to your internal services.
