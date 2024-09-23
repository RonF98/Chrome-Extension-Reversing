# Malicious Capabilities and Applied Protections
As demonstrated in the [Code Analysis](https://github.com/RonF98/Chrome-Extension-Reversing/blob/cd54eb0d0a89dd2d755ee1eadccec7ffc2229708/Reverse%20Analysis/Code%20Analysis.md) section, the extension is capable of the following actions:
* Tab manipulation 
* Unapproved HTTP requests to external domains / redirection
* Storing and exfiltration of search queries
* DOM manipulation

We can see the actor includes multiple protection methods to hide its real capabilities, 
most obviously is the usage of obfuscation throughout the code, variable names such as c,x,s,tu… are meant to to make it difficult for researchers and automated analysis tools to understand the logic behind it. 

Since the extension wants to appear as benign as possible, it needs to minimize any suspicious behavior. This likely explains the complicated requirement: a popup tab must be open during installation for the extension to activate its malicious functions, any other user will have a normal and legit experience.

We can also see the usage of chrome.storage to store the different search queries.
This is likely done to continue the data exfiltration and avoid deletion upon closing the browser (since the chrome.storage can bypass that and keep the data).

# Why this Trigger
After some research online, I found out that BetterTab is a known form of adware and browser hijacker, typically installed through other software bundels like extensions. 
It sets your default page as bettertab.com and hijacks your browser’s search engine by redirecting your search queries through their own engine - ```www.bettertab.xyz```, before landing on the final search page like Bing or Yahoo. We can even see it through debugging:

![image](https://github.com/user-attachments/assets/30944eed-4049-4b84-96a5-6967c38f2639)

Further research revealed that BetterTab is also bundled with another adware that generates 
pop-ups. With this program installed, whenever you browse the internet, an ad from ```try.thebettertab.com``` will randomly appear:
![image](https://github.com/user-attachments/assets/dc401a8a-2b68-48a9-adb2-ee302bb95521)

Clicking on this ad could be a way to trigger the ProDark extension download and since you already have a popup window open, the malicious capabilities will be enabled. 

https://malwaretips.com/blogs/remove-try-thebettertab-com/

# Possible Monetization Tactics
Bad actors often seek easy ways to cash in and monetize their attacks. In this case, they may use the following methods:

- **Affiliate Revenue** – As stated before, the BetterTab domain is a common browser hijacker which redirects traffic to other search engines, this is done to generate revenue by affiliate tracking. Each time BetterTab redirects a user, it includes unique affiliate IDs or tracking parameters (can be see in question 4 in the Burp request). These parameters ensure that any following clicks or purchases made by the user are attributed to the affiliate. In addition, there are also many affiliate-programs that earn cash through generating traffic for a specific domain.

- **Ad Fraud** - The domains ‘bettertab.xyz’ and ‘stttbu.xyz’ could contain ads which 
generate revenue through forced views or clicks. This is a common tactic in ad fraud, where the extension inflates traffic metrics (since the user visits the site in the redirection) and earn money from the advirtisers based on pay-per-view methods.

- **Data Harvesting** – The extension is seen collecting and logging my search queries and history during the redirection process, this data could be then sold to data brokers, 
ad companies, cyber criminals etc.



