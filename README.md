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

1. **The Cloud Shared Responsibility Model** *(Cloud)*: Moving a workload to a cloud provider like AWS or Azure doesn't move all of the security work with it. The provider secures the underlying infrastructure, but the customer is still responsible for things like identity, access, data, and configuration. Exactly where that line falls changes with the deployment model (IaaS, PaaS, or SaaS).

2. **Cloud-Native Security Monitoring** *(Cloud / AI)*: Microsoft Defender for Cloud watches cloud resources for misconfigurations, vulnerabilities, and suspicious activity, extending on-premises monitoring principles into the cloud. Microsoft Sentinel, a cloud-native SIEM, scales log ingestion and search on demand without the hardware planning traditional SIEMs require.

3. **Prompt Injection and Responsible AI** *(AI Security)*: AI tools can be manipulated through hidden instructions buried in untrusted content like emails, documents, or web pages. This is a genuinely new risk specific to AI-assisted work. LLMs can also hallucinate fact-sounding answers that are simply wrong, so AI output needs the same skepticism and human review as any unverified source, and sensitive customer data should never be fed into AI tools carelessly.

4. **Data Governance with DLP, Sensitivity Labels, and Row-Level Security** *(GRC / Cloud)*: Sensitivity labels like "Confidential" or "Highly Restricted" travel with a report and control who can view or export it. DLP policies actively detect patterns like full account numbers and block risky sharing. Row-level security limits each viewer to only the data in their scope. These controls should be designed in from the start, not bolted on at the end.

5. **Compliance-Driven Least Privilege** *(GRC)*: In banking, security controls aren't just best practice. They're regulatory obligations under frameworks like PCI DSS, SOX, GLBA, FFIEC guidance, and NYDFS Part 500. Auditors expect regular access reviews proving accounts hold only the rights they need, quarterly revocation of stale role assignments, and just-in-time (JIT) admin access, which applies least privilege not only to permissions but to time itself.

### 7 Complex Concepts I Didn't Know Before

1. **OAuth2 vs. OpenID Connect**: OAuth2 is an *authorization* protocol. It answers "what can this app do?" but not "who is this user?" OpenID Connect adds an ID token and a user info endpoint on top of OAuth2 to handle *authentication*. Treating OAuth2 alone as a login protocol is a common mistake.

2. **The JWT `alg: none` Attack**: A JSON Web Token's header is only Base64-encoded, so an attacker can change the algorithm field from `RS256` to `none`. If the server doesn't enforce signature verification, it accepts an unsigned, forged token, letting the attacker impersonate any user with no credentials or keys.

3. **VM Escape**: Vulnerabilities in hypervisor memory handling (buffer overflows, use-after-free, or race conditions like the TOCTOU flaw in VMware ESXi) can let an attacker break out of a guest VM and run code on the host. Because a compromised hypervisor exposes every VM it hosts at once, one escape can spread laterally across the whole virtual environment.

4. **Certificate Pinning**: An application can be set to trust only one specific certificate or fingerprint, rejecting any other certificate even if it chains to a trusted Certificate Authority. This defends against attackers who obtain a misissued but technically "valid" certificate.

5. **Harvest Now, Decrypt Later**: Adversaries can capture and store encrypted data today, even without the ability to decrypt it, and wait for future advances (like quantum computing) to break it. Data with a long sensitivity lifespan is at risk now, not just in the future.

6. **MFA Fatigue Attacks**: MFA isn't bulletproof. Attackers who already have a password can spam a user with push notifications until they approve one just to make the prompts stop. Stronger factors like TOTP codes or hardware keys, plus number matching, reduce this risk.

7. **Threat Intelligence Indicator Lifespan**: Indicators of compromise like IP addresses and domains go stale as attackers rotate infrastructure. Indicators need expiration dates, because never expiring them floods analysts with false positives and buries the alerts that actually matter.
