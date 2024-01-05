# Wireguard-Bypass_CGNAT
<h1>Background</h1>
For certain region or country, local ISP are managing your home network using CGNAT(Carrier-grade NAT), which prevents you from doing port-forwarding on your router and expose your home server to the internet. After some research, I found that it is more expensive to host your server on the cloud(based on your CPU and memory requirements), so I made this guide to provide a lower-cost option for those who wants to expose their homelab on the internet.

There are great solutions that is free out there, such as Cloudflare Tunnel, which allow you to expose your homelab without port-forwarding. However, there is a limitation in terms of the protocol(e.g., UDP) allowed to expose, as well as the restriction to run media streaming.

My solution here is to provide a basic setup using an open-source solution called Wireguard and, with the help of a cheap, low-cost VPS(e.g., AWS lightsail) or a lower resource server which has a public IP, to serve as the main gateway to your internal services.

<h1>Steps</h1>

1. Refer to the official guide to install wireguard on both gateway and your homelab: https://www.wireguard.com/install/
2. Further configuration can be done with the steps in here: https://www.wireguard.com/quickstart/
3. Once the above is done, ensure you amend the sysctl.conf file located in <em>'/etc/sysctl.conf'</em>, remove the # from <em>"#net.ipv4.ip_forward=1"</em> on both gateway and homelab.
4. Type <em>"sysctl -p"</em> to apply the change.
5. Transfer the wg0.conf file located in this GitHub to the correct server folder at <em>/etc/wireguard/</em>.
6. Update the information according to the comments in the file.
7. Run <em>"systemctl enable --now wg-quick@wg0"</em> on both server.
8. Verify the service is running using <em>"systemctl status wg-quick@wg0"</em>
9. You may test the port using <em>"python3 -m http.server 8080"</em> and access it from the external site(e.g., 1.2.3.4:8080)
