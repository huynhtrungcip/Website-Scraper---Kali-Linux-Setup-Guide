# Website Scraper - Kali Linux Setup Guide

![Version](https://img.shields.io/badge/Version-1.0-blue)  
![Author](https://img.shields.io/badge/Author-Trung_Huynh-green)   
![License](https://img.shields.io/badge/License-MIT-green)  
![Contributions](https://img.shields.io/badge/Contributions-Welcome-orange)  

## Introduction
This guide walks you through setting up and running the `website-scraper` tool on Kali Linux. By following these steps, you will install the necessary dependencies, configure the environment, and download a demo website using `website-scraper`. We’ll use Node.js and npm as the foundational tools for this project.

## Table of Contents
1. [Prerequisites](#prerequisites)
2. [Step 1: Install Node.js and npm](#step-1-install-nodejs-and-npm)
3. [Step 2: Install `website-scraper`](#step-2-install-website-scraper)
4. [Step 3: Write a Demo Program](#step-3-write-a-demo-program)
5. [Step 4: Run the Program](#step-4-run-the-program)
6. [Step 5: Verify Downloaded Content](#step-5-verify-downloaded-content)

---

## Prerequisites
- Kali Linux installed and updated.
- Basic knowledge of terminal commands.

---

## Step 1: Install Node.js and npm
### 1. Update the system:
```bash
sudo apt update && sudo apt upgrade -y
```

### 2. Install Node.js and npm:
By default, Kali Linux includes Node.js. However, to ensure you have the latest version:
```bash
sudo apt install -y nodejs npm
```

### 3. Verify the installation:
```bash
node -v
npm -v
```

### 4. Update Node.js (if version < 18):
```bash
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install -y nodejs
```

---

## Step 2: Install `website-scraper`
### 1. Create a working directory:
```bash
mkdir ~/website_scraper_demo && cd ~/website_scraper_demo
```

### 2. Initialize a Node.js project:
```bash
npm init -y
```

### 3. Install `website-scraper`:
```bash
npm install website-scraper
```

---

## Step 3: Write a Demo Program
### 1. Create the `scraper.js` file:
```bash
nano scraper.js
```

### 2. Add the following code to the file:
```javascript
import scrape from 'website-scraper';

const options = {
    urls: ['https://example.com'], // Demo website URL
    directory: './downloaded-site', // Directory to save the site
    recursive: true, // Enable recursive download
    maxRecursiveDepth: 2, // Maximum link depth
    sources: [
        {selector: 'img', attr: 'src'},
        {selector: 'link[rel="stylesheet"]', attr: 'href'},
        {selector: 'script', attr: 'src'}
    ],
    requestConcurrency: 5 // Maximum concurrent requests
};

scrape(options)
    .then(() => console.log('Website successfully downloaded!'))
    .catch((err) => console.error('An error occurred:', err));
```

### 3. Save and exit:
Press `CTRL + O`, then `Enter` to save. Press `CTRL + X` to exit.

### 4. Update `package.json` (optional):
Run:
```bash
nano package.json
```
Replace the content with:
```json
{
  "name": "website_scraper_demo",
  "version": "1.0.0",
  "description": "",
  "main": "scraper.js",
  "type": "module",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "website-scraper": "^5.1.0"
  }
}
```

---

## Step 4: Run the Program
### 1. Execute the script:
```bash
node scraper.js
```

### 2. Expected Output:
- On success:
  ```
  Website successfully downloaded!
  ```
- On error:
  ```
  An error occurred: <error details>
  ```

---

## Step 5: Verify Downloaded Content
### 1. List downloaded files:
```bash
ls downloaded-site
```

### 2. View the content in a browser:
Open the following path in your browser:
```
~/website_scraper_demo/downloaded-site
```

---

## Contributions
Contributions are welcome! Please feel free to fork this repository and submit pull requests.

## License
This project is licensed under the MIT License. See the LICENSE file for details.

---

**Happy scraping!**

