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
