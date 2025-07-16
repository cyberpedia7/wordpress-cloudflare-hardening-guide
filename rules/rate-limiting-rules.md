Part 3: Rate Limiting Rules
Rate limiting helps protect your site from brute-force attacks and denial-of-service attempts by limiting the number of requests a single IP address can make in a given period.

Navigate to Rate Limiting: Go to the Security section, select WAF, and then click on Rate limiting rules.

3.1. Rule 1: Protect Login Page
This rule limits the number of login attempts, making it more difficult for attackers to guess your password.

Rule Name: Rate Limit wp-login.php

If URI path...: equals /wp-login.php

When rate exceeds...: 5 requests in 1 minute

Then...: Block for 1 hour

3.2. Rule 2: Protect Admin AJAX
The admin-ajax.php file is used for many functions in the WordPress admin area and can be a target for attacks. This rule limits the rate of requests to this file.

Rule Name: admin-ajax.php

If URI path...: equals /wp-admin/admin-ajax.php

When rate exceeds...: 18 requests in 1 minute

Then...: Block for 1 hour