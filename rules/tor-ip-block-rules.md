<!-- Gradient Banner -->
<p align="center" style="background: linear-gradient(90deg, #1b313a 0%, #47bbc9 100%); padding: 18px 0; border-radius: 10px;">
  <b style="color:#47bbc9; font-size:1.6em;">TOR IP Blocking Rules</b>
</p>

Welcome to the official [**Cyberpedia**](https://cyberpedia.site/) guide for hardening WordPress websites using **Cloudflare's Web Application Firewall (WAF)**.  

<p align="center">
  <a href="../README.md" style="background:#47bbc9; color:#fff; padding:8px 18px; border-radius:6px; text-decoration:none; font-weight:bold;">← Back to README</a>
</p>

---

## <span style="color:#47bbc9">Related Guides</span>
- [Foundational Settings](foundational-settings.md)
- [Custom Firewall Rules](custom-firewall-rules.md)
- [Rate Limiting Rules](rate-limiting-rules.md)

---

## <span style="color:#47bbc9">TOR IP Block Lists</span>
- [tor-block-ips-p1.txt](tor-ip-block-lists/tor-block-ips-p1.txt)
- [tor-block-ips-p2.txt](tor-ip-block-lists/tor-block-ips-p2.txt)
- [tor-block-ips-p3.txt](tor-ip-block-lists/tor-block-ips-p3.txt)
- [tor-block-ips-p4.txt](tor-ip-block-lists/tor-block-ips-p4.txt)
- [tor-block-ips-p5.txt](tor-ip-block-lists/tor-block-ips-p5.txt)

---

Part 4: Block TOR Network IPs
The TOR network can be used to hide the origin of malicious traffic. This rule blocks IP addresses known to be part of the TOR network. Due to expression length limitations in Cloudflare, you will need to create five separate rules.

Instructions
Navigate to Security > WAF > Custom rules and click Create rule.

Create five separate rules with the following details.

Rule 1

Rule Name: TOR Block IPs P1

Expression: ip.src in $tor_ips_part1 (You will need to create a list in Cloudflare with this name and paste the IPs from the file below)

IP List: tor-ip-block-lists/tor-block-ips-p1.txt

Then take action...: Block

Rule 2

Rule Name: TOR Block IPs P2

Expression: ip.src in $tor_ips_part2

IP List: tor-ip-block-lists/tor-block-ips-p2.txt

Then take action...: Block

Rule 3

Rule Name: TOR Block IPs P3

Expression: ip.src in $tor_ips_part3

IP List: tor-ip-block-lists/tor-block-ips-p3.txt

Then take action...: Block

Rule 4

Rule Name: TOR Block IPs P4

Expression: ip.src in $tor_ips_part4

IP List: tor-ip-block-lists/tor-block-ips-p4.txt

Then take action...: Block

Rule 5

Rule Name: TOR Block IPs P5

Expression: ip.src in $tor_ips_part5

IP List: tor-ip-block-lists/tor-block-ips-p5.txt

Then take action...: Block

<p align="center" style="color:#1b313a; font-size: 1.1em;">
  © 2025 [Cyberpedia](https://cyberpedia.site/). All Rights Reserved.
</p>