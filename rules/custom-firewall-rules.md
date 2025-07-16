<!-- Gradient Banner -->
<p align="center" style="background: linear-gradient(90deg, #1b313a 0%, #47bbc9 100%); padding: 18px 0; border-radius: 10px;">
  <b style="color:#47bbc9; font-size:1.6em;">Custom Firewall Rules</b>
</p>

<p align="center">
  <a href="../README.md" style="background:#47bbc9; color:#fff; padding:8px 18px; border-radius:6px; text-decoration:none; font-weight:bold;">← Back to README</a>
</p>

---

## <span style="color:#47bbc9">Related Guides</span>
- [Foundational Settings](foundational-settings.md)
- [Rate Limiting Rules](rate-limiting-rules.md)
- [TOR IP Blocking Rules](tor-ip-block-rules.md)

---

# Part 2: Custom Firewall Rules

With the foundational settings in place, you can now create custom firewall rules to address specific WordPress vulnerabilities.

* **Navigate to Custom Rules:** Go to the **Security** section, select **WAF**, and then click on **Custom rules**. Here, you will create the following rules.

### 2.1. Rule 1: Block PHP Execution in Plugins Folder

This rule prevents direct execution of PHP files in your plugins folder, a common target for attackers.

* **Rule Name:** `Block wp-content/ Plugins`
* **When incoming requests match...:**
    * **Field:** URI Path | **Operator:** contains | **Value:** `/wp-content/plugins/`
    * **And**
    * **Field:** URI Path | **Operator:** ends with | **Value:** `.php`
* **Then take action...:** Block

### 2.2. Rule 2: Block Common Exploit Paths and RFI

This rule blocks requests that attempt to exploit common vulnerabilities, such as remote file inclusion (RFI) and access to sensitive files.

* **Rule Name:** `Block URI Paths - RFI`
* **Expression:**
    ```
    (http.request.uri.path contains "/readme.html") or (http.request.uri.query contains "allow_url_include") or (http.request.uri.query contains "etc/passwd") or (http.request.uri.query eq "<") or (http.request.uri.path contains "/xmlrpc.php")
    ```
* **Then take action...:** Block

### 2.3. Rule 3: Block Empty User-Agent

Legitimate browsers and services almost always include a User-Agent string in their requests. Blocking requests with an empty User-Agent can help filter out malicious bots.

* **Rule Name:** `Block Empty User agent`
* **When incoming requests match...:**
    * **Field:** User Agent | **Operator:** equals | **Value:** (leave this field empty)
* **Then take action...:** Block

### 2.4. Rule 4: Block Known Scanners & Bots

This rule blocks requests from user agents associated with known vulnerability scanners and malicious bots.

* **Rule Name:** `Block User-Agents for Known Scanners`
* **Expression:**
    ```
    (lower(http.user_agent) contains "wpscan") or (lower(http.user_agent) contains "acunetix") or (lower(http.user_agent) contains "nikto") or (lower(http.user_agent) contains "sqlmap") or (lower(http.user_agent) contains "fimap") or (lower(http.user_agent) contains "fuzz faster") or (lower(http.user_agent) contains "netsparker") or (lower(http.user_agent) contains "jaeles") or (lower(http.user_agent) contains "arachni") or (lower(http.user_agent) contains "nmap") or (lower(http.user_agent) contains "nessus") or (lower(http.user_agent) contains "qualys") or (lower(http.user_agent) contains "openvas") or (lower(http.user_agent) contains "owasp zap") or (lower(http.user_agent) contains "dirbuster") or (lower(http.user_agent) contains "dirb") or (lower(http.user_agent) contains "gobuster") or (lower(http.user_agent) contains "xray") or (lower(http.user_agent) contains "nuclei") or (lower(http.user_agent) contains "metasploit") or (lower(http.user_agent) contains "paros") or (lower(http.user_agent) contains "ratproxy") or (lower(http.user_agent) contains "burpsuite") or (lower(http.user_agent) contains "hydra") or (lower(http.user_agent) contains "skipfish") or (lower(http.user_agent) contains "phpshell") or (lower(http.user_agent) contains "scanner") or (lower(http.user_agent) contains "masscan") or (lower(http.user_agent) contains "scan") or (lower(http.user_agent) contains "zgrab") or (lower(http.user_agent) contains "immuniweb") or (lower(http.user_agent) contains "whatweb") or (lower(http.user_agent) contains "Penthouse Critical Path") or (http.user_agent eq "") or (lower(http.user_agent) contains "astra web security scanner") or (lower(http.user_agent) contains "python" and not (http.host eq "workflow.cyberpedia.site"))
    ```
* **Then take action...:** Block
