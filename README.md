![image](https://github.com/user-attachments/assets/36f8999b-b8c8-48d7-a4eb-6761a19fd4b7)

# Content Table
1. [ProDark.crx - Download Chrome Extension](ProDark.crx)
2. [ProDark.zip - Extracted Source Code](ProDark.zip)
3. [Reverse Engineering](https://github.com/RonF98/Chrome-Extension-Reversing/tree/36b9226cb485e18f783b7d0935d0442fdb0f9be4/Reverse%20Engineering)
   - [CRX content](https://github.com/RonF98/Chrome-Extension-Reversing/blob/c5f0936837ad3eb84a7dd87137dc12c22a542e23/Reverse%20Engineering/CRX%20Content.md)
   - [Code Analysis](https://github.com/RonF98/Chrome-Extension-Reversing/blob/c5f0936837ad3eb84a7dd87137dc12c22a542e23/Reverse%20Engineering/Code%20Analysis.md)
   - [Purpose and Monetization](https://github.com/RonF98/Chrome-Extension-Reversing/blob/c5f0936837ad3eb84a7dd87137dc12c22a542e23/Reverse%20Engineering/Purpose%20and%20Monetization.md)

# Description
In this reverse engineering analysis, we'll investigate the ProDark Chrome extension, which claims to provide a simple dark mode for websites. By dissecting its CRX file and analyzing it's key components, we'll uncover the obfuscated code designed to hide its **true malicious capabilities**, triggered only under specific conditions. The extension can redirect user search queries through external domains, manipulates Tabs and alters DOM elements on the webpage. This analysis sheds light on the sophisticated techniques used by malicious Chrome extensions to bypass detection while monetizing unsuspecting users browsing activity.

# Benign Usage
In its default usage, the ProDark Chrome extension functions as a simple tool to toggle dark mode on web pages. When activated, it changes the background to black and text to white, providing a basic dark theme for easier viewing. 
It achieves that by leveraging its content.js script, which runs on every web page the user visits. This script listens for messages from the extension's background.js script to toggle dark mode. When triggered, it manipulates the DOM by altering the background-color property of page elements to black and the color property of text elements to white. 
This functionality appears straightforward, with the extension responding to user actions through its content script to apply or remove dark mode across different sites.
![image](https://github.com/user-attachments/assets/c59cf856-8327-4f98-af29-ca4b4b8d1db8)
![image](https://github.com/user-attachments/assets/83494913-dcba-45a5-af99-8e6598b2113f)

# Installation
Since the extension was removed from the chrome webstore, i've included the .crx file for download and installation.
1. Download the CRX file
2. Open chrome://extensions/ in your browser
3. Upload the file directly
