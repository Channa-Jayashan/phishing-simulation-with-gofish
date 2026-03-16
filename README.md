\# Phishing Simulation with GoPhish



A hands-on phishing simulation lab using \*\*GoPhish\*\* on Kali Linux to demonstrate social engineering attack techniques, credential harvesting, email tracking, and campaign analytics — all in a controlled, ethical environment.



\## Project Overview



\- \*\*Objective\*\*: Execute a full phishing simulation (setup, template creation, campaign launch, and results analysis) to showcase offensive security tooling and awareness training concepts.

\- \*\*Duration\*\*: Completed in one session (detailed walkthrough documented here).

\- \*\*Tools/Environment\*\*: 

&nbsp; - Host: Windows (bridge mode networking)

&nbsp; - Guest: Kali Linux VM (bridged — same IP subnet as host)

&nbsp; - Tool: GoPhish (open-source phishing framework)

&nbsp; - SMTP: Gmail with App Password

&nbsp; - Target: Self-owned test email account only

\- \*\*Repo Structure\*\*:

&nbsp; - `screenshots/`: Step-by-step visuals of GoPhish interface and results

&nbsp; - `errors-faced/`: Any network/firewall/SMTP issues encountered (empty if none)

\- \*\*Key Focus\*\*: Ethical simulation only — no real users targeted.



\## Lab Setup Facts



| Aspect              | Details                                      | Notes / Screenshot Reference                  |

|---------------------|----------------------------------------------|-----------------------------------------------|

| Hypervisor          | VMware / VirtualBox / Hyper-V                | Kali VM in bridge mode                        |

| Kali IP             | Dynamic via bridge (e.g., 192.168.x.x)       | Used in campaign URL                          |

| GoPhish Admin       | https://localhost:3333 (Kali localhost)      | Self-signed cert accepted                     |

| Phishing Listener   | http://<KALI\_IP>:80                          | External URL for campaign links               |

| Sending Profile     | Gmail SMTP (smtp.gmail.com:587 / 465)        | App Password required                         |

| Target Group        | 1 test recipient (self-owned email)          | Manual entry                                  |



\## Step-by-Step Walkthrough



\### 1. Launch \& Secure GoPhish



Started GoPhish binary on Kali → accessed admin panel → immediately changed default password for security.



1\. Launched via terminal or menu.

2\. Viewed initial credentials in console output.

3\. Accessed https://localhost:3333 → accepted self-signed cert.

4\. Logged in → updated password.



!\[Launch terminal output](screenshots/01\_launch-and-login/launch-terminal.png)  

!\[Admin login \& dashboard after password change](screenshots/01\_launch-and-login/login-dashboard.png)



\### 2. Sending Profile Configuration



Created SMTP profile using Gmail → tested delivery successfully.



1\. Navigated to Sending Profiles → New Profile.

2\. Configured Gmail SMTP (smtp.gmail.com, port 587, TLS, App Password).

3\. Saved → sent test email to self.

4\. Verified receipt in inbox.



!\[Creating new sending profile](screenshots/02\_sending-profile/creating-new-profile.png)  

!\[Test mail configuration](screenshots/02\_sending-profile/profile-test-mail-config.png)  

!\[Test email received in inbox](screenshots/02\_sending-profile/test-mail-received.png)



\### 3. Landing Page Creation



Built a credential-harvesting page (e.g., Google login clone).



1\. Imported HTML from legitimate site source.

2\. Enabled "Capture Submitted Data" and "Capture Passwords".

3\. Set redirect URL to real site after submission.

4\. Saved and verified.



!\[New landing page created with capture options](screenshots/03\_landing-page/new-landing-page-created.png)



\### 4. Email Template Setup



Crafted realistic phishing email.



1\. Imported raw email source (headers + body).

2\. Used "Change Links" to redirect all URLs to phishing landing page.

3\. Added tracking image for open detection.

4\. Previewed and saved.



!\[Imported raw email template](screenshots/04\_email-template/imported-raw-template.png)  

!\[Final template after link changes \& tracking](screenshots/04\_email-template/new-template-after-change-links.png)



\### 5. Users \& Groups



Defined test target.



1\. Created new group.

2\. Added single test recipient (name + email).

3\. Saved.



!\[New target group with test recipient](screenshots/05\_users-groups/new-target-group.png)



\### 6. Campaign Launch \& Results Analysis



Executed the full simulation and monitored outcomes.



1\. Created new campaign → selected template, landing page, sending profile, group.

2\. Set URL base to http://<KALI\_IP>.

3\. Launched campaign.

4\. Monitored real-time dashboard: email sent → opened → clicked → credentials submitted.

5\. Viewed captured data and timeline.



!\[New campaign setup](screenshots/06\_campaign-and-results/new-campaign-setup.png)  

!\[Phishing email preview](screenshots/06\_campaign-and-results/phishing-email-preview.png)  

!\[Campaign launched dashboard](screenshots/06\_campaign-and-results/campaign-launched-dashboard.png)  

!\[Results timeline view](screenshots/06\_campaign-and-results/results-timeline.png)  

!\[Clicked link \& interaction results](screenshots/06\_campaign-and-results/clicked-link-results.png)  

!\[Captured compromised credentials](screenshots/06\_campaign-and-results/compromised-credentials.png)  

!\[Simulation complete overview](screenshots/06\_campaign-and-results/simulation-complete-overview.png)



\## Troubleshooting \& Observations



\- \*\*Gmail App Password mandatory\*\* — normal password fails due to security policies.

\- \*\*Listener binding\*\* — ensure GoPhish runs with `--admin-listen=0.0.0.0:3333 --phish-listen=0.0.0.0:80` if accessing from host (or use Kali localhost for admin).

\- \*\*Network / Firewall\*\* — Bridge mode worked smoothly; no major blocks. Any issues saved in `errors-faced/` folder.

\- \*\*Redirect effectiveness\*\* — Post-submit redirect to legitimate site helps maintain realism.

\- \*\*Ethical reminder\*\* — Simulation used only self-controlled test accounts.



This repo serves as a clean reference for GoPhish workflow in authorized red teaming or security training scenarios.



Feel free to clone and adapt for your own ethical labs.



⭐ Star if this helped your phishing tooling journey!

