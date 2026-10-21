# cybersecurityforprofessionals

## Course Reflection

### Top 3 Quotes I Remember

1. **"Develop a passion for learning."**
   This line opened nearly every week of the course. Threats, tools, and best practices change constantly, so the most important skill in this field is the habit of continuing to learn.

2. **"A rule set that has never been tested is only a hypothesis, not a working control."**
   From the Next-Generation Firewalls week. Writing a firewall rule is not the same as proving it works. Controls have to be tested, including negative tests that confirm they block what they should.

3. **"Isolation must be configured, not assumed."**
   From the Virtualization and Container Foundations week. Virtual machines and containers feel separate, but that separation only holds if it is deliberately configured, hardened, and monitored.

### 5 Technical Concepts That Interested Me

1. **Defense in Depth on Linux**: Layering controls such as file permissions (for example, making sure `/etc/shadow` is never world-readable), disabling unneeded kernel modules, automated patching, and auditing so that no single failure exposes the whole system.

2. **TLS and Forward Secrecy**: How a TLS handshake uses Diffie-Hellman / Elliptic Curve Diffie-Hellman to negotiate session keys without ever sending the secret over the wire, and why TLS 1.3 mandates forward secrecy so past sessions stay safe even if long-term keys are later compromised.

3. **Firewall Rule Ordering and Shadowing**: A broad "allow" rule placed above a specific "deny" rule shadows it, so the deny is never reached. A rule set can pass syntax checks and still be functionally broken if policy order isn't verified.

4. **Detecting Password Spray Attacks in Splunk**: Searching for failed logins across all accounts in a short time window, grouped by source IP. One IP failing against dozens of accounts is a spray campaign, while a single failed login is usually just a typo. The response scales with the pattern, not the single event.

5. **AI-Assisted Security Operations**: Using Microsoft Security Copilot and the Defender XDR Alert Triage and Phishing Triage agents to help Tier 1 analysts prioritize alerts faster, while keeping a human in the loop to review and validate what the AI recommends.

### 7 Complex Concepts I Didn't Know Before

1. **OAuth2 vs. OpenID Connect**: OAuth2 is an *authorization* protocol. It answers "what can this app do?" but not "who is this user?" OpenID Connect adds an ID token and a user info endpoint on top of OAuth2 to handle *authentication*. Treating OAuth2 alone as a login protocol is a common mistake.

2. **The JWT `alg: none` Attack**: A JSON Web Token's header is only Base64-encoded, so an attacker can change the algorithm field from `RS256` to `none`. If the server doesn't enforce signature verification, it accepts an unsigned, forged token, letting the attacker impersonate any user with no credentials or keys.

3. **VM Escape**: Vulnerabilities in hypervisor memory handling (buffer overflows, use-after-free, or race conditions like the TOCTOU flaw in VMware ESXi) can let an attacker break out of a guest VM and run code on the host. Because a compromised hypervisor exposes every VM it hosts at once, one escape can spread laterally across the whole virtual environment.

4. **Certificate Pinning**: An application can be set to trust only one specific certificate or fingerprint, rejecting any other certificate even if it chains to a trusted Certificate Authority. This defends against attackers who obtain a misissued but technically "valid" certificate.

5. **Harvest Now, Decrypt Later**: Adversaries can capture and store encrypted data today, even without the ability to decrypt it, and wait for future advances (like quantum computing) to break it. Data with a long sensitivity lifespan is at risk now, not just in the future.

6. **MFA Fatigue Attacks**: MFA isn't bulletproof. Attackers who already have a password can spam a user with push notifications until they approve one just to make the prompts stop. Stronger factors like TOTP codes or hardware keys, plus number matching, reduce this risk.

7. **Threat Intelligence Indicator Lifespan**: Indicators of compromise like IP addresses and domains go stale as attackers rotate infrastructure. Indicators need expiration dates, because never expiring them floods analysts with false positives and buries the alerts that actually matter.
