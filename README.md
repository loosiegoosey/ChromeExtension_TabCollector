## Overview

Overview
The Chrome Extension Tab Collector is a simple yet powerful tool designed to help users organize and manage their browser tabs efficiently. By utilizing the extension, users can save groups of URLs, assign titles to these groups, and easily access them later, consequently improving their productivity and browser performance.

##
## Features

Features
- **Effortless URL Grouping**: Save the current set of open tabs as a group.
- **Title Assignment**: Assign custom titles to each group of saved URLs for quick access.
- **Persistent Storage**: Saved URL groups are stored using Chrome's `storage.sync`, allowing for easy retrieval even after browser restarts.
- **Name-Based Filtering**: Automatically filters out unwanted or duplicate Chrome tabs.

##
## Installation Instructions

Installation Instructions

### Prerequisites
Ensure you have the latest version of Google Chrome installed.

### Step-by-Step Guide
1. **Clone the Repository**:
    ```bash
    git clone https://github.com/nitishprabhu26/ChromeExtension_TabCollector.git
    ```
2. **Load the Extension**:
    - Open Chrome and navigate to `chrome://extensions/`.
    - Enable the "Developer mode" toggle on the top right corner.
    - Click the "Load unpacked" button.
    - Select the cloned repository folder.

That's it! The extension should now appear in your Chrome extensions list.

##
## Usage Examples

Usage Examples
### Saving a Group of Tabs
1. Open the extension popup.
2. Enter a descriptive title in the `urls-group-title` input field.
3. Press `Enter` to save the current set of tabs under the provided title.

Upon saving, you will see the list of URLs stored in the extension's storage.

```javascript
document.getElementById("urls-group-title").addEventListener("keypress",
    function(e){
        if(e.key === "Enter"){
            chrome.runtime.sendMessage({title: e.target.value});
        }
    }
);
```

### Retrieving Saved Groups
When accessing the extension, it will automatically load and display your saved URL groups, allowing you to quickly navigate to any set of tabs you have previously saved.

```javascript
chrome.storage.sync.get(["urlLists"], (obj) => {
    console.log(obj);
});
```

##
## Code Summary

Code Summary

### Key Files
- **content-script.js**:
  - Listens for keypress events on the `urls-group-title` input field.
  - Sends messages to the background script when the "Enter" key is pressed, containing the title of the URL group.
  - Retrieves and displays saved URL groups using Chrome's storage API.
  
- **script.js**:
  - Listens for messages containing titles from the content script.
  - Retrieves the current window and its tabs.
  - Filters out unnecessary Chrome tabs, saving only the significant ones under the provided title.

##
## License

License
This project is licensed under the MIT License. Feel free to use, modify, and distribute as needed.

```markdown
MIT License

Permission is hereby granted, free of charge, to any person obtaining a copy
 of this software and associated documentation files (the "Software"), to deal
 in the Software without restriction, including without limitation the rights
 to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
 copies of the Software, and to permit persons to whom the Software is
 furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
 copies or substantial portions of the Software. THE SOFTWARE IS PROVIDED "AS IS",
 WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO
 THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
 IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES
 OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
 OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
```
```

This README.md file provides a comprehensive overview of the Chrome Extension Tab Collector project. It includes details on what the project does, key features, installation instructions, usage examples, a summary of the code structure, and licensing information.