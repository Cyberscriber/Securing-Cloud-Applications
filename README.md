<h1>Securing Cloud Applications</h1>


 <h2>Description</h2>
Developed and designed a cyber-blog web application using Azure’s Cloud services and Docker.  Protected the web application by utilizing Azure’s Security features, such as Azure’s Front Door, WAF, and Security Center.
</b>
</b>

<h2>Environments Used </h2>

- <b>Azure: Keyvaults, App Services, Front Door, WAF,  PHP, HTML, Docker, OpenSSL</b> 

<h2>Program walk-through:</h2>
Describe/Summarize your Project
I used Microsoft Azure (https://portal.azure.com) to build and host my own “cyber-blog” web application. I then applied Azure’s security features to protect it. 
What were your project Requirements?
Our requirements included:
Hosting the web application using Azure’s Cloud Services
Using Azure’s App Service resource to create the web application
Choosing a domain with Azure
Deploying a Docker container which had a framework for a blog webpage
SSHing  into the container to customize the webpage
Creating a Self-signed certificate with OpenSSL 
Storing the certificate in Azure’s Key vault
After determining the security issues with a self-signed certificate, creating and binding a managed CA approved certificate to the web application
Deploying Azure’s Front Door, and configuring a WAF rule to restrict traffic from certain countries
Analyzing the Azure’s Security Center recommendations and applying the recommended fix




What were the advantages for choosing Azure’s App Service resource, instead of creating a Virtual Machine From scratch?


Using Azure App Service, we can pass responsibility of managing features outside of the web application to the cloud service provider
In other words, we are only responsible for deploying and managing their web application and it's associated data
Deploying web applications can be done much faster, as user's don't have to be concerned about configuring their OS
The user doesn't have to worry about the OS and middleware maintenance, such as installing software updates and patching
Azure App services are cheaper to run than Virtual machines
Azure App services have built in features for securing and hosting a web application, such as DNS, Web App Firewalls, Domain purchasing, SSL certification binding.


What were the security issues you encountered when you used a self-signed certificate?
A Self-signed certificate is a certificate that has not been signed by a certificate authority. While these certificates are simple to create, and have no expense almost all browsers will alert the user visiting the webpage that is signed with a self-signed certificate that the webpage is not trusted by a Certificate Authority in the browser’s root store and to proceed with caution. 


How did you address that security concern?
I created and bound a managed certificate provided by Azure, as this is a trusted certificate which has been approved by a CA which most browsers trust.


What is Azure’s Front Door, and how did you use its WAF feature?
Azure’s Front Door is a  Cloud Resource, it resides in front of my web application to protect it. It works on the Application Layer of the OSI Model (Layer 7). Its primary solution is a load balancer. It can incorporate a Web Application Firewall (WAF) to protect against web vulnerabilities attacks.  With the WAF, I applied a custom rule to protect against web requests from countries that I wasn't expecting any traffic from.  This could help protect against potential attacks where I knew I wasn't expecting any visitors.


What is Azure’s Security Center, and how did you apply its features?
Azure Security Center is a management system that provides best practices and   recommendations to enhance the security of your cloud resources. When I checked it, it had several security recommendations with various criticalities. One recommendation was to require FTP access into the web application with FTPS, which is the encrypted version of FTP.


<p align="center">
<br/>
<img src="https://imgur.com/VZSp492.png" height="80%" width="80%" alt="Azure Steps"/>
<br />
<br />
What is the IP address of your webpage? Under Custom Domains, in Azure, I see that the IP address of my webpage is
(Ip Address and Domain Id removed from screenshot):  <br/>
<img src="https://imgur.com/HVPNjHN.png" height="80%" width="80%" alt="Azure Steps"/>
<br />
<br />
Run a DNS lookup on your website. What does the NS record show?: <br/>
<img src="https://imgur.com/5HRqdMp.png" height="80%" width="80%" alt="Azure Steps"/>
<br />
<br />
<p align="center">
What is the location (city, state, country) of your IP address? Des Moines, Iowa, United States<br />
https://whatismyipaddress.com/ip/<br />
<br />
When creating your web app, you selected a runtime stack.  What was it? Does it work on the front end or the back end? <br /> PHP 7.4   Back-end
PHP is a programming language for back end development only<br />
<br />
Inside the /var/www/html directory, there was another directory called assets. Explain what was inside that directory.   CSS and style.css: <br/>
<img src="https://imgur.com/vaJwnqk.png" height="80%" width="80%" alt="Azure Steps"/>
<br />
<br />
After completing the Day 2 activities, view your SSL certificate and answer the following questions:
Is your browser returning an error for your SSL certificate? No Why or why not? 
The Certificate is valid because I used the free version, so Azure provided the certificate
:  <br/>
<img src="https://imgur.com/yesRsR3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
What is the validity of your certificate (date range)? <br />The date range shows 7/7/2021 thru 7/7/2022
Do you have an intermediate certificate? If so, what is it?<br />
Yes, Issued to Microsoft RSA TLS CA 02.  Microsoft RSA TLS CA 02 is part of the DSRE TLS CA hierarchy and issues SHA2 end-entity certificates<br />
<br />
Do you have a root certificate? If so, what is it? <br/>
Yes, Issued to Baltimore Cyber Trust Root:  <br/>
<img src="https://imgur.com/TSJ8ZlB.png" height="80%" width="80%" alt="Azure Steps"/>
<br />
<br />
CyberTrust was founded as a subsidiary of GTE Corporation's Government Systems Information Security Directorate. It focused on security services for electronic commerce. These included authentication, privacy, integrity and non-repudiation using Public Key Encryption technology.:  <br/>
<img src="https://imgur.com/miFnGOV.png" height="80%" width="80%" alt="Azure Steps"/>
<br />
<br />
What are the similarities and differences between Azure Web Application Gateway and Azure Front Door? <br/>
Similarities:  Both reside in front of your web application in order to protect it. ● They work on the Application Layer (7) of the OSI model. ● Their primary solution is a load balancer. ● They can incorporate a web application firewall (WAF) to protect against web vulnerability attacks. ● They have additional features such as URL path-based routing and SSL/TLS termination. <br/>
Differences:<br/>
The Web Application Gateway is more regional, to protect a web application in a single region in your cloud. ● The Azure Front Door is more global and is better suited when you have a variety of regions in a cloud environment.  <br/>
<br />
A feature of the Web Application Gateway and Front Door is “SSL Offloading.” What is SSL offloading? What are its benefits? <br/>
<br />
SSL offloading is the process of removing the SSL based encryption from incoming traffic that a web server receives to relieve it from decryption of data. Security Socket Layer (SSL) is a protocol that ensures the security of HTTP traffic and HTTP requests on the internet. <br/>
Benefits:<br/>
Boost the page load speed time.
Faster response from the Web server.
Better web server performance.
Enhance the stability of the website.
Auto-scaling the web servers during the peak hours of traffic.
Use as a load balancer for serving web traffic using different servers.<br/>
<br/>
<br/>
Include screenshots below to demonstrate that your web app has the following:<br/>
Azure Front Door enabled <br/>
<img src="https://imgur.com/EpyLlbe.png" height="80%" width="80%" alt="Azure Steps"/>
<br />
<br />
A WAF custom rule:<br />
<img src="https://imgur.com/uyb340b.png" height="80%" width="80%" alt="Azure Steps"/>
<br />
<br />
<img src="https://imgur.com/cibJGjw.png" height="80%" width="80%" alt="Azure Steps"/>
<br />
<br />
<img src="https://imgur.com/WOmDYGh.png" height="80%" width="80%" alt="Azure Steps"/>
<br />
<br />
 
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
