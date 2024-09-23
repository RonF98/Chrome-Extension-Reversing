# Description
In this reverse engineering analysis, we'll investigate the ProDark Chrome extension, which claims to provide a simple dark mode for websites. By dissecting its CRX file and analyzing it's key components, we'll uncover the obfuscated code designed to hide its true malicious capabilities, triggered only under specific conditions. The extension can redirect user search queries through external domains, manipulates Tabs and alters DOM elements on the webpage. This analysis sheds light on the sophisticated techniques used by malicious Chrome extensions to bypass detection while monetizing unsuspecting users browsing activity.

# Benign Usage
In its default usage, the ProDark Chrome extension functions as a simple tool to toggle dark mode on web pages. When activated, it changes the background to black and text to white, providing a basic dark theme for easier viewing. 
It achieves that by leveraging its content.js script, which runs on every web page the user visits. This script listens for messages from the extension's background.js script to toggle dark mode. When triggered, it manipulates the DOM by altering the background-color property of page elements to black and the color property of text elements to white. 
This functionality appears straightforward, with the extension responding to user actions through its content script to apply or remove dark mode across different sites.
![image](https://github.com/user-attachments/assets/edf68868-dcdf-40b7-9f49-f796cffe3b9d)
![image](https://github.com/user-attachments/assets/b927b948-0e32-4fa4-9820-41228de54fa3)
