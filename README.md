\# Phishing Simulation with GoPhish



Walkthrough of a complete \*\*GoPhish\*\* phishing simulation performed on \*\*Kali Linux\*\* (running in a bridged VM).  

Follows the steps from the tutorial: \[Penetration Testing: Gophish Tutorial (Phishing Framework)](https://youtu.be/dktthMkQF-Q) by Loi Liang Yang.



\*\*Environment\*\*  

\- Host: Windows  

\- Guest: Kali Linux (bridged networking — same subnet)  

\- GoPhish version: \[add version if you remember, e.g. v0.12.x or latest]  

\- Phishing URL base: http://YOUR\_KALI\_IP (example: http://192.168.1.105)  

\- Admin interface: https://localhost:3333 (on Kali)



\*\*Important Notes\*\*  

\- This is for \*\*authorized penetration testing / red teaming / security awareness training only\*\*.  

\- Gmail was used with an \*\*App Password\*\* for the sending profile.  

\- All targets were test accounts I own — no real users were targeted.



\## Step-by-step Walkthrough



\### 1. Launch \& Secure GoPhish



Started the binary → accessed admin panel → changed default password immediately.



!\[Launch terminal](screenshots/01\_launch-and-login/launch-terminal.png)  

!\[Admin login \& dashboard](screenshots/01\_launch-and-login/login-dashboard.png)



\### 2. Sending Profile (SMTP)



Created Gmail-based profile with App Password → tested successfully.



!\[Creating profile](screenshots/02\_sending-profile/creating-new-profile.png)  

!\[Test configuration](screenshots/02\_sending-profile/profile-test-mail-config.png)  

!\[Test email received](screenshots/02\_sending-profile/test-mail-received.png)



\### 3. Landing Page



Imported Google-style login clone → enabled credential capture → set redirect to real site.



!\[Landing page creation](screenshots/03\_landing-page/new-landing-page-created.png)



\### 4. Email Template



Imported raw email source → used "Change Links" to point to our landing page → added tracking pixel.



!\[Imported template](screenshots/04\_email-template/imported-raw-template.png)  

!\[Final template after link changes](screenshots/04\_email-template/new-template-after-change-links.png)



\### 5. Users \& Groups



Created test group with one recipient (my test email).



!\[Target group](screenshots/05\_users-groups/new-target-group.png)



\### 6. Campaign Launch \& Results



Launched campaign → monitored real-time → captured click + credential submission.



!\[New campaign setup](screenshots/06\_campaign-and-results/new-campaign-setup.png)  

!\[Email preview](screenshots/06\_campaign-and-results/phishing-email-preview.png)  

!\[Dashboard after launch](screenshots/06\_campaign-and-results/campaign-launched-dashboard.png)  

!\[Timeline view](screenshots/06\_campaign-and-results/results-timeline.png)  

!\[Click results](screenshots/06\_campaign-and-results/clicked-link-results.png)  

!\[Captured credentials](screenshots/06\_campaign-and-results/compromised-credentials.png)  

!\[Simulation complete](screenshots/06\_campaign-and-results/simulation-complete-overview.png)



\## Lessons / Observations



\- Bridge mode worked well — no major network issues (add any errors you faced here if any).

\- App Password is mandatory for Gmail.

\- Redirect + realistic template reduces suspicion significantly.



Feel free to clone and use as reference for your own authorized simulations.



⭐ If this helped, give it a star!

