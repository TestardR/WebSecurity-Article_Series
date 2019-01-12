Number 1: Injection attacks 

What is it ? 

According to Ian Muscat (2017) Injection attacks refer to a broad class of " attack vectors that allow an attacker to supply untrusted input to a program, which gets processed by an interpreter as part of a command or query which alters the course of execution of that program.". 

Injections are listed as the number one web application security risk in the OWASP Top 10. Injection attacks are widespread, particularly in SQL injections (SQLi) and Cross-site Scripting XSS), but they can take many forms (SQL, LDAP, XPath, or NoSQL queries, OS commands, XML parsers, SMTP headers, expression languages, and ORM queries).

How can you be attacked ? 

Any source of data can be an injection vector. "Injection flaws occur when an attacker can send hostile data to an interpreter." (OWASP, 2017). In short, anyone can send hostile data through any source of data. 

Through which weaknesses ?

According to OWASP (2017) Injection flaws are prevalent in legacy code, not readily updated to modern security standards. Furthermore, scanners and fuzzers (fuzz testing : it involves inputting massive amounts of data in an attempt to find flaws) can help attackers find injection flaws. 

For what impact ? 

According to Andrew van der Stock (Pluralsight, 2018), even though injections are less common, their impact is off the charts. They cover data loss, corruption, or disclosure to unauthorized parties, loss of accountability, or denial of access. Injection can sometimes lead to complete host takeover. 


OWASP (2017), Top 10-2017 A1-Injection, url: 
https://www.owasp.org/index.php/Top_10-2017_A1-Injection

Muscat I. (April 2017)., What are Injection Attacks?, 
url : https://www.acunetix.com/blog/articles/injection-attacks/

van der Stock, A. (April 2018). Play by play: OWASP Top 10 2017, Pluralsight. url: https://app.pluralsight.com/library/courses/play-by-play-owasp-top-ten-2017 



















Number 2 : Broken Authentication

What is it ? 

According to Lauren Pagalos (2018), many websites require users to login to access their accounts, make a purchase, etc. It is often, done using a username and password. With this data, a site assigns and sends each logged in visitor a unique session ID that serves as a key to the user’s identity on the server. If not properly secured, a broken authentication scheme would allow an attacker to impersonate a valid user. 

How can you be attacked ? 

Automation plays a great part in these attacks. Attackers have access to hundreds of millions of valid username and password combinations for credential stuffing, default administrative account lists, automated brute force, and dictionary attack tools (OWASP 2017). 

Furthermore, session management attacks are widespread. Attackers may hijack authcookies (authentication cookies send to users by servers) or unexpired session tokens. 

Through which weaknesses ?

Authentication is a widespread implementation on the web. Session management is present in all stateful applications. Attackers can detect broken authentication manually and exploit them through fuzzers injection password list or dictionary attacks. 

For what impact ?  

These attacks can escalate quickly as attackers can compromise the whole system accessing a few accounts or just one admin account.


OWASP (2017), Top 10-2017 A2-Broken Authentication
https://www.owasp.org/index.php/Top_10-2017_A2-Broken_Authentication

Pagalos L. (August, 2018), The OWASP Top 10: Broken Authentication & Session Management, url: https://www.sitelock.com/blog/2018/08/owasp-top-10-broken-authentication-session-management/
























Number 3 : Sensitive Data Exposure

What is it ? 

According to Linus Särud (2016), Sensitive Data Exposure occurs when an application does not adequately protect sensitive information. The data can vary and anything from passwords, session tokens, credit card data to private health data and more can be exposed. 

How can you be attacked ? 

Attackers don't often directy attack crypted data. Rather, they "steal keys, execute man-in-the-middle attacks, or steal clear text data off the server, while in transit, or from the user’s client." (OWASP, 2017). 

Through which weaknesses ?

1) The most widespread flaw is simply not encrypting sensitive data. 

2) When data is encrypted, "weak key generation and management, and weak algorithm, protocol and cipher usage is common, particularly for weak password hashing storage techniques." (OWASP, 2017) 

3) For data in transit, server side weaknesses are mainly easy to detect, and subject to injection attacks. 

For what impact ? 

At worse, all flaws will compromise all data that should have been protected.  

OWASP (2017), Top 10-2017 A3-Sensitive Data Exposure, url: 
https://www.owasp.org/index.php/Top_10-2017_A3-Sensitive_Data_Exposure

Särud L. (July 2016), OWASP TOP 10: Sensitive Data Exposure, 
url: https://blog.detectify.com/2016/07/01/owasp-top-10-sensitive-data-exposure-6/




























Number 4 : XML External Entities (XXE)

What is it ?

According to Faisal Tameesh (2016 ) XML Extenal Entities is a type of attack against an application that parses XML input. This attack occurs when XML input containing a reference to an external entity is processed by a weakly configured XML parser (A parser is a compiler or interpreter component that breaks data into smaller elements for easy translation into another language).
 
XML is a widespread data format found in everything from web services (XML-RPC, SOAP, REST, etc.) to documents (XML, HTML, DOCX) and image files (SVG, EXIF data, etc.) use XML. Where there is XML, there is an XML parser (Muscat, 2017). 

How can you be attacked ? 

In short, attackers can exploit vulnerable XML parsers if they can upload XML or include hostile content in an XML document, exploiting vulnerable code, dependencies or integrations (OWASP, 2017). 

Through which weaknesses ?

Older XML parsers allow specification of an external entity, allowing for the add-on of malicius payloads. On parsing, the malicious payload will get run (F5 DevCentral, 2018). Tools, such as SAST or DAST can help for flaw detections in XML parsers (OWASP, 2017). 

For what impact ?

These flaws can be used to extract data, execute a remote request from the server, scan internal systems, perform a denial-of-service attack, as well as execute other attacks (OWASP, 2017). 

F5 DevCentral (January, 2018), OWASP Top 10: XML External Entities, 3:05 minutes, url: https://www.youtube.com/watch?v=g2ey7ry8_CQ

OWASP (2017), Top 10-2017 A4-XML External Entities (XXE), 
url: https://www.owasp.org/index.php/Top_10-2017_A4-XML_External_Entities_(XXE)

Muscat I. (July, 2017). What Is XML External Entity (XXE)?, url: https://dzone.com/articles/what-is-xml-external-entity-xxe

Tameesh F. (November, 2016). Exploitation: XML External Entity (XXE) Injection, url: https://depthsecurity.com/blog/exploitation-xml-external-entity-xxe-injection




















Number 5 : Broken Access Control

What is it ?

Access control, sometimes called authorization, is how a web application grants access to content and functions to some users and not others. According to Kiuwan (2018), “broken access means that unauthorized access to system functionality and resources has created exploitable weakness that opens your company to harmful and potentially expensive outcomes.”. 

How can you be attacked ? 

According to OWASP (2017), even though SAST and DAST tools wan detect the absence of access control, they cannot verify if it is functional when present. Access control is primarily detectable using manual means. However, it is possibly discoverable through automation for the absence of such in certain frameworks. 

Through which weaknesses ?

“Access control weaknesses are common due to the lack of automated detection, and lack of effective functional testing by application developers.” (OWASP, 2017).

For what impact ?

“The technical impact is attackers acting as users or administrators, or users using privileged functions, or creating, accessing, updating or deleting every record.” (OWASP, 2017).


OWASP (2017), Top 10-2017 A5-Broken Access Control, url: https://www.owasp.org/index.php/Top_10-2017_A5-Broken_Access_Control

Kiuwan (2018) OWASP Top 10 2017 – A5 Broken Access Control, 
url: https://www.kiuwan.com/blog/owasp-top-10-2017-a5-broken-access-control/




























Number 6 : Security Misconfiguration

What is it ?

Security Misconfiguration arises when Security settings are defined, implemented, and maintained. Good security requires a secureconfiguration defined and deployed for the application, web server, database server, and platform . Misconfiguration can include both errors in the installation of security, and the complete failure to install available security controls (Application Security Series, 2018).

How can you be attacked ? 

Attackers will often attempt to exploit unpatched flaws or access default accounts, unused pages, unprotected files and directories, etc to gain unauthorized access or knowledge of the system. 

Through which weaknesses ?

According to OWASP (2017), security misconfiguration can happen at any level of an application stack (network services, platform, web server, application server, database, frameworks, custom code, and pre-installed virtual machines, containers, or storage). Automated scanners are useful for detecting misconfigurations.

For what impact ?

“Such flaws frequently give attackers unauthorized access to some system data or functionality. Occasionally, such flaws result in a complete system compromise.” (OWASP 2017). 

OWASP (2017), Top 10-2017 A6-Security Misconfiguration, 
url: https://www.owasp.org/index.php/Top_10-2017_A6-Security_Misconfiguration

Application Seucrity Series, (July 2018). Security Misconfiguration, a conscious element of OWASP Top 10, the risks and solutions, url: https://www.htbridge.com/blog/OWASP-security-misconfiguration.html





























Number 7 : Top 10-2017 A7-Cross-Site Scripting (XSS)

What is it ?

According to OWASP (2018), Cross-Site Scripting (XSS) attacks are a type of injection, in which malicious scripts are injected into websites. XSS attacks occur when an attacker uses a web application to send malicious code.

How can you be attacked ? 

According to OWASP (2017), automated tools can detect and exploit all three forms of XSS, and there are freely available exploitation frameworks. 

There are three forms of XSS : 
1. Reflected XSS:  The application or API includes unvalidated and unescaped user input as part of HTML output. A successful attack can allow the attacker to execute arbitrary HTML and JavaScript in the victim’s browser.  
2. Stored XSS: The application or API stores unsanitized user input that is viewed at a later time by another user or an administrator. 
3. DOM XSS: JavaScript frameworks, single-page applications, and APIs that dynamically include attacker-controllable data to a page are vulnerable to DOM XSS.  

Through which weaknesses ?

See the above forms of XSS to point out potential weaknesses. Furthermore, automated tools can find some XSS problems automatically, particularly in mature technologies such as PHP, J2EE / JSP, and ASP.NET (OWASP, 2017). 

For what impact ?

“The impact of XSS is moderate for reflected and DOM XSS, and severe for stored XSS, with remote code execution on the victim's browser, such as stealing credentials, sessions, or delivering malware to the victim.” (OWASP, 2017).

OWASP (2017), Top 10-2017 A7-Cross-Site Scripting (XSS), 
url : https://www.owasp.org/index.php/Top_10-2017_A7-Cross-Site_Scripting_(XSS)

OWASP (2018), Cross-site Scripting (XSS), 
url: https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)





















Number 8 : Insecure Deserialization

What is it ?

According to Acutenix (2017) insecure Deserialization is a vulnerability which occurs when untrusted data is used to send malicious payloads upon it being deserialized 

“Serialization refers to a process of converting an object into a format which can be persisted to disk (for example saved to a file or a datastore), sent through streams (for example stdout), or sent over a network.The format in which an object is serialized into, can either be binary or structured text (for example XML, JSON YAML…). 

Deserialization on the other hand, is the opposite of serialization, that is, transforming serialized data coming from a file, stream or network socket into an object.” (Acutenix, 2017). 

How can you be attacked ? 

Attackers have to exploit deserialization flaws. According to OWASP (2017), it is somewhat difficult, as off the shelf exploits rarely work without changes to underlying exploit code. 

Through which weaknesses ?

According to OWASP (2017), some tools can discover deserialization flaws, but human assistance is frequently adjust the underlying exploit codes. It is expected that prevalence data for deserialization flaws will increase as tooling is developed to help identify and address it. 

For what impact ?

"These flaws can lead to remote code execution attacks, one of the most serious attacks possible." (OWASP, 2017). 

Acutenix (December, 2017), What is Insecure Deserialization?, 
url : https://www.acunetix.com/blog/articles/what-is-insecure-deserialization/

OWASP (2017), Top 10-2017 A8-Insecure Deserialization, 
url: https://www.owasp.org/index.php/Top_10-2017_A8-Insecure_Deserialization























Number 9 : Using Components with Known Vulnerabilities

What is it ?

According to Rami Sass (2018), known vulnerabilities are vulnerabilities that were discovered in open source components and published. From the moment of publication , a vulnerability can be exploited by hackers who find the documentation. 

How can you be attacked ? 

According to OWASP (2017), while it is easy to find already-written exploits for many known vulnerabilities, other vulnerabilities require concentrated effort to develop a custom exploit.  A such, attackers may produce custom exploits for specific web applications.

Through which weaknesses ?

According to OWASP (2017), modern web applications are getting component-heavy, which can lead to development teams to not even understand which components they use in their applicationI, much less keeping them up to date. Some scanners such as retire.js help in detection, but determining exploitability requires additional efforts. 

For what impact ?

“While some known vulnerabilities lead to only minor impacts, some of the largest breaches to date have relied on exploiting known vulnerabilities in components. “ (OWASP, 2017).

OWASP (2017), Top 10-2017 A9-Using Components with Known Vulnerabilities, url: https://www.owasp.org/index.php/Top_10-2017_A9-Using_Components_with_Known_Vulnerabilities

Sass R. (June, 2018), OWASP A9: Using Components With Known Vulnerabilities - Why You Can't Ignore It, url: https://resources.whitesourcesoftware.com/blog-whitesource/owasp-a9-using-components-with-known-vulnerabilities




























Number 10 : Insufficient Logging & Monitoring

What is it ?

According to Linus Särud (2018), insufficient Logging and Monitoring covers the lack of best practices that should be in place to prevent or damage control security breaches. The category includes everything from unlogged events, logs that are not stored properly and warnings where no action is taken within reasonable time. 

How can you be attacked ? 

According to OWASP (2017), “Exploitation of insufficient logging and monitoring is the bedrock of nearly every major incident. Attackers rely on the lack of monitoring and timely response to achieve their goals without being detected.".

Through which weaknesses ?

The best strategy for determining if your web applications have sufficient monitorig and logging is to examine the logs following penetrationg testing. The testers' actions should be recorded sufficiently and promptly. 

For what impact ?

According to Ponemon Institute – IBM (2017, p. 4), in 2016, identifying a breach took an average of 191 days – plenty of time for damage to be inflicted. “Most successful attacks start with vulnerability probing. Allowing such probes to continue can raise the likelihood of successful exploit to nearly 100%.” (OWASP, 2017).


OWASP (2017), Top 10-2017 A10-Insufficient Logging&Monitoring, 
url: https://www.owasp.org/index.php/Top_10-2017_A10-Insufficient_Logging%26Monitoring

Penomon Institute (June 2017), 2017 Cost of Data Breach Study, 
url: https://www-01.ibm.com/common/ssi/cgi-bin/ssialias?htmlfid=SEL03130WWEN&

Särud L. (July 2016), OWASP TOP 10: Insufficient Logging and Monitoring, 
url: https://blog.detectify.com/2018/04/06/owasp-top-10-insufficient-logging-monitoring/









