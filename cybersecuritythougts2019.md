INDUSTRY OVERVIEW

According to Andrew van der Stock (Pluralsight, April 2018), two major changes are affecting the web development industry. First of all, developers are pushing a lot of server logic towards the client's, making more prone to attacks, as logic can more easily be leaked. Second of all, developers are moving to cloud services, which implies moving the state from the application to the cloud. Security has always been about protecting the state. It is now been moved around, and it is a huge change for security.
As far as browser security goes, the internet is safer but we are far away from a secure world. According to Alexa Top 1 Million Analysis (Scott Helme, August 2018), HTTPS has reached an increasing 51% of the top 1 Million websites, which is great news. HTTP Strict Transport Security (HSTS), forcing browsers to only interact with HTTPS connections, reaches an increasing 12.75%. Only 3.5% uses Content Security Policy (CSP). It increases steadily. Finally, Public Key Pinning is decreasing to a tiny 0.86% of the top 1 Million. It has deprecated by Google as it has been misused causing "website suicide".

van der Stock, A. (april 2018). Play by play: OWASP Top 10 2017, Pluralsight. url: https://app.pluralsight.com/library/courses/play-by-play-owasp-top-ten-2017

Helme, S. (August 2018). Alexa Top 1 Million Analysis - August 2018, url: https://scotthelme.co.uk/alexa-top-1-million-analysis-august-2018/

TOP 3 CRITCAL WEB APPLICATION SECURITY RISKS

According to OWASP (2017), the three major security risks face by developers are 1. Injection, 2. Broken Authentication, 3. Sensitive Data Exposure.
1. Even though the likelihood of SQL injection has considerably dropped, the rise of NoSQL databases (such as MongoDB) has given momentum to NoSQL injections. Developers have to prepare for this. SQL or NoSQL excluded, injections can have a huge impact and cannot be discarded.
2. Password breached is very common. Passwords chosen by users are too often duplicates and easy to breach. "123456" is an example of a typical password used over 22 390 492 times up to 2018 (haveibeenpwned.com, 2018). Technology should move towards making passwords reusable or different. Furthermore, users have to be informed if they have been breached.
3. Data protection has be enhanced to meet regulations, such the EU GDPR (2018). Indeed, sexual orientation, health records, bank credentials or even political affiliation are critical to users. "Rather than directly attacking crypted contents, attackers steal keys, execute man-inthe-middle attacks, or steal clear text data off the server, while in transit, or from the user’s client (often the browser)." (OWASP, 2018, p. 9). Data has to be properly protected.

OWASP (2017). OWASP Top 10 - 2017, The Ten Most Critical Web Application Security Risks, url: https://www.owasp.org/images/7/72 

haveibeenpwned.com (december 2018). Pwned Passwords. url: https://haveibeenpwned.com/Passwords

NEXT STEPS ?

1. CI/CD has to be enhanced and monitored. Continuous integration, continuous deployment as well as unit testing are at the cornerstone of cybersecurity for developers. Technologies such as Mocha and Jest for testing or Appveyor and Travis for continuous integration are widespread. Well programmed and implemented, they will allow developers to protect users from evolving attacks.
2. Business developers should produce metrics to point out issues regarding security threats. They should be quick to set security standards and quality training for their developers.
3. Developers should move to or update their new frameworks. Technologies such as Angular and React are built upon the latest technology standards. They integrate built-in protection for modern attacks, such as injections. That is why injections are less common, not because developers actually learned how to deal with them...

Romain Testard
