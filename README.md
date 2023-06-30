# Selenium-Practice


Certainly! Here's an example of a test script for Node.js using Puppeteer to automate the login process on Gmail:

```javascript
const puppeteer = require('puppeteer');

(async () => {
  try {
    // Launch a new browser instance
    const browser = await puppeteer.launch();

    // Create a new page
    const page = await browser.newPage();

    // Navigate to Gmail login page
    await page.goto('https://www.gmail.com');

    // Fill in the login form
    await page.type('input[type="email"]', 'your-email@gmail.com'); // Replace with your Gmail email address
    await page.click('div[id="identifierNext"]');

    // Wait for the password field to be visible
    await page.waitForSelector('input[type="password"]');

    // Fill in the password
    await page.type('input[type="password"]', 'your-password'); // Replace with your Gmail password
    await page.click('div[id="passwordNext"]');

    // Wait for the Gmail inbox page to load
    await page.waitForNavigation({ waitUntil: 'networkidle0' });

    // Perform actions or assertions on the logged-in page
    const pageTitle = await page.title();
    console.log('Logged-in page title:', pageTitle);

    // Close the browser
    await browser.close();
  } catch (error) {
    console.error('An error occurred:', error);
  }
})();
```

In this example, we use Puppeteer to automate the login process on Gmail. 

After launching the browser and creating a new page, we use `page.goto()` to navigate to the Gmail login page. 

Next, we fill in the email address by using `page.type()` and click the next button. We wait for the password field to be visible with `page.waitForSelector()`. Then, we fill in the password and click the next button.

After successfully logging in, we wait for the Gmail inbox page to load using `page.waitForNavigation()`. You can perform additional actions or assertions on the logged-in page based on your requirements.

Finally, we close the browser with `browser.close()`. We also wrap the entire script inside a try-catch block to handle any errors that may occur during the execution.

Remember to replace `'your-email@gmail.com'` with your actual Gmail email address and `'your-password'` with your Gmail password before running the script.
