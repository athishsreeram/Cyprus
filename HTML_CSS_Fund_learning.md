# 1-Week Plan: HTML & CSS Fundamentals for Cypress Learning

**Goal:**  
Learn HTML structure and CSS selectors in one week (2-3 hours daily) to prepare for Cypress testing. You’ll be able to inspect webpages and write basic Cypress selectors like `cy.get('#id')`.

---

## Day 1: HTML Basics - Structure & Tags

**Time:** 2-3 hours  
**Objective:** Understand HTML and common tags.  
**Topics:** HTML purpose, structure (`<!DOCTYPE html>`, `<html>`), tags (`<h1>`, `<input>`).

### Learning Plan

- **Read (30 min):**
  - [W3Schools - HTML Intro](https://www.w3schools.com/html/html_intro.asp)
  - [W3Schools - Basic HTML](https://www.w3schools.com/html/html_basic.asp)
  
- **Practice (1-2 hr):**
  - Use a text editor (e.g., VS Code) or [CodePen](https://codepen.io).
  - Write the following code:

    ```html
    <!DOCTYPE html>
    <html>
    <head>
      <title>My Page</title>
    </head>
    <body>
      <h1>Welcome</h1>
      <p>This is a test page.</p>
      <button>Click Me</button>
    </body>
    </html>
    ```
  - Save as `index.html`, open in a browser, and add `<input>` and `<a>` tags.
  
- **Cypress Connection:**  
  Tags are targets for `cy.get()`.

---

## Day 2: HTML Attributes & Forms

**Time:** 2-3 hours  
**Objective:** Learn attributes and form elements.  
**Topics:** `id`, `class`, `name`, forms (`<form>`, `<input>`).

### Learning Plan

- **Read (30 min):**
  - [W3Schools - HTML Attributes](https://www.w3schools.com/html/html_attributes.asp)
  - [W3Schools - HTML Forms](https://www.w3schools.com/html/html_forms.asp)
  
- **Practice (1-2 hr):**
  - Create the following form:

    ```html
    <form>
      <input id="username" type="text" name="user">
      <input id="password" type="password" name="pass">
      <button type="submit">Login</button>
    </form>
    ```
  - Add placeholder text as needed and test in a browser.
  
- **Cypress Connection:**  
  Use selectors such as `cy.get('#username')` or `cy.get('input[name="user"]')`.

---

## Day 3: CSS Basics - Styling & Selectors Intro

**Time:** 2-3 hours  
**Objective:** Learn CSS and basic selectors.  
**Topics:** CSS syntax, selectors (`p`, `.class`, `#id`).

### Learning Plan

- **Read (30 min):**
  - [W3Schools - CSS Intro](https://www.w3schools.com/css/css_intro.asp)
  - [W3Schools - CSS Syntax](https://www.w3schools.com/css/css_syntax.asp)
  
- **Practice (1-2 hr):**
  - Add the following style to your `index.html`:

    ```html
    <style>
      h1 { color: blue; }
      .highlight { background-color: yellow; }
      #username { border: 1px solid black; }
    </style>
    <body>
      <h1>Welcome</h1>
      <p class="highlight">This is a test.</p>
      <input id="username" type="text">
    </body>
    ```
  - Test the styling in your browser.
  
- **Cypress Connection:**  
  Use selectors like `cy.get('.highlight')` to target styled elements.

---

## Day 4: CSS Selectors - Advanced Targeting

**Time:** 2-3 hours  
**Objective:** Master selectors for Cypress.  
**Topics:** Attribute selectors (`[type="text"]`), child selectors (`div > p`).

### Learning Plan

- **Read (30 min):**
  - [W3Schools - CSS Selectors](https://www.w3schools.com/css/css_selectors.asp)
  
- **Practice (1-2 hr):**
  - Expand your HTML with the following:

    ```html
    <div class="form-container">
      <input type="text" class="input-field required">
      <button class="btn submit">Submit</button>
    </div>
    <style>
      .input-field { padding: 5px; }
      [type="text"] { width: 200px; }
      .form-container > button { color: green; }
    </style>
    ```
  - Check the styles in your browser.
  
- **Cypress Connection:**  
  Use selectors like `cy.get('.input-field')` or `cy.get('input[type="text"]')`.

---

## Day 5: Using Browser DevTools

**Time:** 2-3 hours  
**Objective:** Inspect elements for Cypress selectors.  
**Topics:** DevTools, finding IDs/classes.

### Learning Plan

- **Watch (30 min):**
  - [YouTube - Chrome DevTools Crash Course](https://www.youtube.com/watch?v=34MBi9Ri1TU) (freeCodeCamp snippet)
  
- **Practice (1-2 hr):**
  - Visit [The Internet - Login](https://the-internet.herokuapp.com/login).
  - Inspect the page:
    - **Username:** `id="username"`
    - **Button:** `class="radius"`
  - Write the following Cypress commands:

    ```javascript
    cy.get('#username').type('test');
    cy.get('.radius').click();
    ```
  
- **Cypress Connection:**  
  Use DevTools to find selectors for `cy.get()`.

---

## Day 6: Practice Project - Build & Inspect

**Time:** 2-3 hours  
**Objective:** Combine HTML/CSS skills and prepare for Cypress testing.

### Task

- **Build the following page:**

  ```html
  <!DOCTYPE html>
  <html>
  <head>
    <title>QA Practice</title>
    <style>
      .container { border: 2px solid gray; padding: 10px; }
      #submit-btn { background-color: blue; color: white; }
      .error { color: red; display: none; }
    </style>
  </head>
  <body>
    <div class="container">
      <h2>Login</h2>
      <input id="email" type="text" class="field">
      <input id="pass" type="password" class="field">
      <button id="submit-btn">Login</button>
      <p class="error">Wrong credentials</p>
    </div>
  </body>
  </html>
  ```
  
- **Practice:**
  - Inspect the page using DevTools to identify `#email`, `.field`, and `#submit-btn`.
  
- **Cypress Connection:**  
  Example test commands:

  ```javascript
  cy.get('#email').type('user@example.com');
  cy.get('#submit-btn').click();
  cy.get('.error').should('be.visible');
  ```

---

## Day 7: Review & Test Prep

**Time:** 2-3 hours  
**Objective:** Solidify your skills and start working with Cypress.

### Learning Plan

- **Review (1 hr):**
  - [W3Schools - HTML Elements](https://www.w3schools.com/html/html_elements.asp)
  - [W3Schools - CSS Selectors](https://www.w3schools.com/css/css_selectors.asp)
  - Quiz yourself: When to use `#id` vs. `.class`? How do you target `<input type="text">`?
  
- **Apply to Cypress (1-2 hr):**
  - **Install Cypress:**  
    ```bash
    npm install cypress --save-dev
    ```
  - **Test [The Internet - Login](https://the-internet.herokuapp.com/login):**

    ```javascript
    // cypress/e2e/first_test.cy.js
    describe('Login Test', () => {
      it('enters credentials', () => {
        cy.visit('https://the-internet.herokuapp.com/login');
        cy.get('#username').type('tomsmith');
        cy.get('#password').type('SuperSecretPassword!');
        cy.get('button.radius').click();
        cy.get('#flash').should('contain', 'You logged into');
      });
    });
    ```
  - **Run Cypress:**  
    ```bash
    npx cypress open
    ```
    
- **Cypress Connection:**  
  You’re now ready to integrate HTML/CSS skills into your Cypress tests!

---

## Resources Summary

**W3Schools:**
- [HTML Intro](https://www.w3schools.com/html/html_intro.asp)
- [HTML Basic](https://www.w3schools.com/html/html_basic.asp)
- [HTML Attributes](https://www.w3schools.com/html/html_attributes.asp)
- [HTML Forms](https://www.w3schools.com/html/html_forms.asp)
- [HTML Elements](https://www.w3schools.com/html/html_elements.asp)
- [CSS Intro](https://www.w3schools.com/css/css_intro.asp)
- [CSS Syntax](https://www.w3schools.com/css/css_syntax.asp)
- [CSS Selectors](https://www.w3schools.com/css/css_selectors.asp)

**Practice Sites:**
- [CodePen](https://codepen.io)
- [The Internet - Login](https://the-internet.herokuapp.com/login)

**Video:**
- [Chrome DevTools Crash Course](https://www.youtube.com/watch?v=34MBi9Ri1TU)

---

## Tips

- **Daily Practice:** Adjust code snippets each day.  
- **Browser:** Use Chrome for DevTools.  
- **Next:** Learn JavaScript basics after this week.

---
