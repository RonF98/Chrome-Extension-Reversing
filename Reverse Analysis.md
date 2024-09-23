# CRX File
When extracting the CRX file, we see it contains the following files: 
- manifest.json
- content.js
- background.js
- _metadata (folder)
- logo.png  

> **manifest.json** - This file outlines the metadata of the extension. It declares the name "ProDark", its purpose (providing dark mode for simple pages), and the associated background script (background.js) and content script (content.js). It also lists the **permissions for storage and tabs**.  

> **content.js** - This script runs on every web page and applies the dark mode functionality. It changes the background color to black and the text color to white. It listens for messages to toggle dark mode and can reset the background color depending on specific conditions.  

> **background.js** - This file manages background processes, including the extension's behavior when the user clicks on the icon. It also contains functions for converting and manipulating color values, along with event listeners for toggling the extension's badge and sending messages to content scripts.  

> **_metadata** - This folder which contains the verified_contents.json file, is part of Chrome’s security framework to ensure the authenticity and integrity of extensions distributed through its Web Store.  

> **logo.png** - contains the extension’s icon logo.

From this general overview, we can see that the extension requests the storage and tabs permissions, and contains a substantial background.js file with nearly 2,000 lines of code, which seem unusual for an extension that only claims to change colors.

# 
