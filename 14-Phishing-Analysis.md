#  Phishing
Spam and Phishing are common social engineering attacks. In social engineering, phishing attack vectors can be a phone call, a text message, or an email. As you should have already guessed, our focus is on email as the attack vector. 
Phishing is a serious attack vector that you, as a defender, will have to defend against.

The invention of the email dates back to the 1970s for ARPANET. So, what makes up an email address?

- User Mailbox (or Username)
- @
- Domain

Let's look at the following email address, billy@johndoe.com.
- The user mailbox is billy
- @ (thanks Ray)
- The domain is johndoe.com

Below is a checklist of the pertinent information an analyst (you) is to collect from the email header:
- Sender email address
- Sender IP address
- Reverse lookup of the sender IP address
- Email subject line
- Recipient email address (this information might be in the CC/BCC field)
- Reply-to email address (if any)
- Date/time

Afterward, we draw our attention to the email body and attachment(s) (if any).
Below is a checklist of the artifacts an analyst (you) needs to collect from the email body:
- Any URL links (if an URL shortener service was used, then we'll need to obtain the real URL link)
- The name of the attachment
- The hash value of the attachment (hash type MD5 or SHA256, preferably the latter)

Warning: Be careful not to click on any links or attachments in the email accidentally. 


##  Phishing Anaylysis Tools

###  Email Header Analysis

- [Google Admin Toolbox](https://toolbox.googleapps.com/apps/messageheader/analyzeheader)
- [Message Header Analyzer](https://mha.azurewebsites.net/)
- [Analyze my mail header](https://mailheader.org/)
- [ipinfo](https://ipinfo.io/)
- [PhishTool](https://www.phishtool.com/)
- [Virustotal](https://www.virustotal.com/gui/home/upload)
- [urlscan.io](https://urlscan.io/)
- [Talos](https://talosintelligence.com/reputation)
- [Talos File Reputation](https://talosintelligence.com/talos_file_reputation)
- [Spamhaus](https://www.spamhaus.org/)
- [PhishTank](https://phishtank.com/)
- [Mxtoolbox](https://mxtoolbox.com/)


##  Phishing Prevention
There are various actions a defender can take to help protect the users from falling victim to a malicious email. 

Some examples of these actions are listed below:

- Email Security (SPF, DKIM, DMARC)
- SPAM Filters (flags or blocks incoming emails based on reputation)
- Email Labels (alert users that an incoming email is from an outside source)
- Email Address/Domain/URL Blocking (based on reputation or explicit denylist)
- Attachment Blocking (based on the extension of the attachment)
- Attachment Sandboxing (detonating email attachments in a sandbox environment to detect malicious activity)
- Security Awareness Training (internal phishing campaigns)


###   Sender Policy Framework
Sender Policy Framework (SPF) is used to authenticate the sender of an email. With an SPF record in place, Internet Service Providers can verify that a mail server is authorized to send email for a specific domain. An SPF record is a DNS TXT record containing a list of the IP addresses that are allowed to send email on behalf of your domain.

How does a basic SPF record look like?

- `v=spf1 ip4:127.0.0.1 include:_spf.google.com -all`

An explanation for the above record:

- `v=spf1` -> This is the start of the SPF record
- `ip4:127.0.0.1` -> This specifies which IP (in this case version IP4 & not IP6) can send mail
- `include:_spf.google.com` -> This specifies which domain can send mail
- `-all` -> non-authorized emails will be rejected

Tool to check SPF status - [dmarcian for SPF](https://dmarcian.com/spf-survey/)

###  DKIM (DomainKeys Identified Mail)
DKIM stands for DomainKeys Identified Mail and is used for the authentication of an email that’s being sent. Like SPF, DKIM is an open standard for email authentication that is used for DMARC alignment. A DKIM record exists in the DNS, but it is a bit more complicated than SPF. DKIM’s advantage is that it can survive forwarding, which makes it superior to SPF and a foundation for securing your email.

How does a DKIM record look like?

- `v=DKIM1; k=rsa; p=MIIBIjANBgkqhkiG9w0B`

An explanation of the above record:

- `v=DKIM1` -> This is the version of the DKIM record. This is optional. 
- `k=rsa` -> This is the key type. The default value is RSA. RSA is an encryption algorithm (cryptosystem).
- `p=` -> This is the public key that will be matched to the private key, which was created during the DKIM setup process. 

###  Domain-based  Message Authentication Reporting, & Conformance
DMARC, (Domain-based  Message Authentication Reporting, & Conformance) an open source standard, uses a concept called alignment to tie the result of two other open source standards, SPF (a published list of servers that are authorized to send email on behalf of a domain) and DKIM (a tamper-evident domain seal associated with a piece of email), to the content of an email. If not already deployed, putting a DMARC record into place for your domain will give you feedback that will allow you to troubleshoot your SPF and DKIM configurations if needed.

How does a basic DMARC record look like?

- `v=DMARC1; p=quarantine; rua=mailto:postmaster@website.com`

An explanation of the above record:

- `v=DMARC1` -> Must be in all caps, and it's not optional
- `p=quarantine` -> If a check fails, then an email will be sent to the spam folder (DMARC Policy)
- `rua=mailto:postmaster@website.com` -> Aggregate reports will be sent to this email address

- [DMARC Checker](https://dmarcian.com/domain-checker/)


###  S/MIME (Secure/Multipurpose internet Mail Extensions)
S/MIME (Secure/Multipurpose internet Mail Extensions) is a widely accepted protocol for sending digitally signed and encrypted messages.
The 2 main ingredients for S/MIME are:
- Digital Signatures
- Encryption
