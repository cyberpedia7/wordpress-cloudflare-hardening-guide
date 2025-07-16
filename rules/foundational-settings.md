<!-- Gradient Banner -->
<p align="center" style="background: linear-gradient(90deg, #1b313a 0%, #47bbc9 100%); padding: 18px 0; border-radius: 10px;">
  <b style="color:#47bbc9; font-size:1.6em;">Foundational Settings</b>
</p>

Welcome to the official [**Cyberpedia**](https://cyberpedia.site/) guide for hardening WordPress websites using **Cloudflare's Web Application Firewall (WAF)**.  

<p align="center">
  <a href="../README.md" style="background:#47bbc9; color:#fff; padding:8px 18px; border-radius:6px; text-decoration:none; font-weight:bold;">← Back to README</a>
</p>

---

## <span style="color:#47bbc9">Related Guides</span>
- [Custom Firewall Rules](custom-firewall-rules.md)
- [Rate Limiting Rules](rate-limiting-rules.md)
- [TOR IP Blocking Rules](tor-ip-block-rules.md)

---

Part 1: Foundational Cloudflare Settings
Before diving into custom rules, it's crucial to establish a secure baseline. These initial settings form the foundation of your website's defense.

1.1. Set SSL/TLS Encryption Mode
A secure connection is the first line of defense. The SSL/TLS encryption mode ensures that all data transferred between your website and its visitors is encrypted and secure.

Step 1: Log in to your Cloudflare account and navigate to the SSL/TLS section, then click on the Overview tab.

Step 2: Set the encryption mode to Full (Strict). This provides the highest level of security by encrypting traffic from the visitor to Cloudflare and from Cloudflare to your server.

1.2. Enable Managed Rulesets
Cloudflare's managed rulesets are collections of pre-configured rules that protect your site from a wide range of common attacks.

Step 1: Go to the Security section, select WAF, and then click on Managed rules.

Step 2: Enable the Cloudflare Managed Ruleset. This ruleset is designed to block malicious traffic and is regularly updated by Cloudflare's team of security experts.

Step 3: Enable the OWASP ModSecurity Core Rule Set. This ruleset provides protection against the most common types of attacks, as defined by the Open Web Application Security Project (OWASP).

<p align="center" style="color:#1b313a; font-size: 1.1em;">
  © 2025 [Cyberpedia](https://cyberpedia.site/). All Rights Reserved.
</p>
