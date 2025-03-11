
# Must-Have Skills to Learn Cypress (QA Beginners)

## 1. Core Technical Skills

### Basic JavaScript Knowledge
**Why:** Cypress tests are written in JavaScript. You don’t need to be a pro, but you need the basics.

**What to Learn:**
- Variables: `let name = "testuser";`
- Functions: `function login() { ... }`
- Objects: `{ username: "test", password: "123" }`
- Arrays: `["item1", "item2"]`
- Conditionals: `if (x > 0) { ... }`

**Example in Cypress:**
```javascript
it('logs in', () => {
  let user = "testuser";
  cy.get('#username').type(user);
});
```
**How to Learn:** FreeCodeCamp’s "JavaScript Basics" or Codecademy’s free JS intro (1-2 weeks).

---

### HTML & CSS Fundamentals
**Why:** You’ll use HTML structure and CSS selectors to find elements on a webpage (e.g., `cy.get('#id')`).

**What to Learn:**
- Tags: `<input>`, `<button>`, `<div>`
- IDs/Classes: `<input id="username" class="form-input">`
- Attributes: `<button type="submit">`
- CSS Selectors: `#id`, `.class`, `tag[attribute="value"]`

**Example in Cypress:**
```javascript
cy.get('.login-btn').click();         // Find by class
cy.get('input[name="email"]').type('test@example.com'); // By attribute
```
**How to Learn:** W3Schools HTML/CSS tutorials (1 week).

---

### Understanding Web Applications
**Why:** Cypress tests how users interact with web apps, so you need to know what’s happening on a page.

**What to Learn:**
- **Page Elements:** Buttons, forms, links, tables.
- **Browser Basics:** URL changes, page loads.
- **DevTools:** Inspect elements (right-click → Inspect in Chrome).

**Example:**
Inspect a login button to find its ID or class for `cy.get()`.

**How to Learn:** Play with a site like [The Internet](https://the-internet.herokuapp.com) and use browser DevTools (2-3 days).

---

### Basic QA Concepts
**Why:** Cypress is a QA tool, so you need to think like a tester.

**What to Learn:**
- **Test Cases:** “What happens if I enter a wrong password?”
- **Assertions:** Verify results (e.g., “error message appears”).
- **Positive/Negative Testing:** Valid vs. invalid inputs.

**Example in Cypress:**
```javascript
it('shows error on wrong password', () => {
  cy.get('#password').type('wrong');
  cy.get('button').click();
  cy.get('.error').should('be.visible');
});
```
**How to Learn:** Read “QA 101” articles or watch YouTube QA intros (1 week).

---

## 2. Nice-to-Have Skills (Grow Into These)

### Intermediate JavaScript
**Why:** For complex tests, custom commands, or API handling.

**What to Learn:**
- **Promises:** `.then(response => { ... })`
- **Async/await:** `async () => { await cy.request() }`
- **Loops:** `for (let i = 0; i < 5; i++) { ... }`

**Example:**
```javascript
cy.request('GET', '/api/users').then((response) => {
  expect(response.body.length).to.be.greaterThan(0);
});
```
**How to Learn:** Practice with free JS challenges (e.g., LeetCode easy problems).

---

### API Testing Basics
**Why:** Many apps (e.g., fintech in Cyprus) rely on APIs, and Cypress can test them.

**What to Learn:**
- **HTTP Methods:** `GET`, `POST`
- **Status Codes:** `200 (OK)`, `404 (Not Found)`
- **JSON:** `{ "status": "success" }`

**Example:**
```javascript
cy.request('POST', '/api/login', { user: 'test' })
  .its('status')
  .should('eq', 200);
```
**How to Learn:** Postman free course or Cypress docs on `cy.request()` (1-2 weeks).

---

### Version Control (Git)
**Why:** Teams use Git to manage test code, especially in jobs.

**What to Learn:**
- **Commands:** `git clone`, `git add`, `git commit`, `git push`

**Example:**
```bash
git add my_test.cy.js
git commit -m "Add login test"
git push
```
**How to Learn:** GitHub’s “Git Basics” guide (1 week).

---

### Agile/Testing Tools Exposure
**Why:** QA roles often use agile methods and tools like Jira.

**What to Learn:**
- **Agile:** Sprints, user stories.
- **Tools:** Jira (bug tracking), CI/CD (e.g., Jenkins basics).

**How to Learn:** Free agile intros online or job shadowing (optional for now).

---

## 3. Soft Skills

### Problem-Solving
**Why:** QA is about finding bugs and verifying fixes.

**Example:**  
*"Why isn’t this button clickable? Check the selector."*

**How to Learn:** Practice breaking down small problems.

---

### Attention to Detail
**Why:** Spotting tiny differences (e.g., text color, error text).

**Example:**  
```javascript
cy.get('.msg').should('have.text', 'Logged in') // Correct  
cy.get('.msg').should('have.text', 'Loged in') // Incorrect  
```
**How to Learn:** Test real apps and compare expected vs. actual.

---

## 4. Learning Path (Timeline)

- **Week 1-2:** HTML/CSS (selectors) + Basic JS (variables, functions).
- **Week 3:** Install Cypress, write a simple test (e.g., login).
- **Week 4:** Add assertions + practice on a demo site.
- **Month 2:** Learn APIs + custom commands.
- **Month 3:** Git basics + intermediate JS (optional).

---

## 5. Example: Putting It Together

Here’s a test using core skills:

```javascript
describe('Login Tests', () => {
  it('logs in successfully', () => {
    cy.visit('https://the-internet.herokuapp.com/login');
    cy.get('#username').type('tomsmith');        // HTML + JS
    cy.get('#password').type('SuperSecretPassword!');
    cy.get('button').click();                    // Interaction
    cy.get('.flash.success').should('be.visible'); // Assertion + QA
  });
});
```

---

## 6. Why These Skills Matter

- **Cypress-Specific:** JS, HTML/CSS, and web app knowledge let you write and debug tests.
- **QA Career:** API, Git, and soft skills prep you for jobs (e.g., Cyprus fintech QA roles).
- **Beginner-Friendly:** Start with the core, grow into the rest.

---

## 7. What’s Your Next Step?
Want help with a specific skill (e.g., JS basics) or a sample test to practice? Let me know!

---

### Version Control (Git)
**Why:** Teams use Git to manage test code, especially in jobs.

**What to Learn:**
- **Commands:** `git clone`, `git add`, `git commit`, `git push`

**Example:**
```bash
git add my_test.cy.js
git commit -m "Add login test"
git push
```
**How to Learn:** GitHub’s “Git Basics” guide (1 week).

---

### Agile/Testing Tools Exposure
**Why:** QA roles often use agile methods and tools like Jira.

**What to Learn:**
- **Agile:** Sprints, user stories.
- **Tools:** Jira (bug tracking), CI/CD (e.g., Jenkins basics).

**How to Learn:** Free agile intros online or job shadowing (optional for now).

---

## 3. Soft Skills

### Problem-Solving
**Why:** QA is about finding bugs and verifying fixes.

**Example:**  
*"Why isn’t this button clickable? Check the selector."*

**How to Learn:** Practice breaking down small problems.

---

### Attention to Detail
**Why:** Spotting tiny differences (e.g., text color, error text).

**Example:**  
```javascript
cy.get('.msg').should('have.text', 'Logged in') // Correct  
cy.get('.msg').should('have.text', 'Loged in') // Incorrect  
```
**How to Learn:** Test real apps and compare expected vs. actual.

---

## 4. Learning Path (Timeline)

- **Week 1-2:** HTML/CSS (selectors) + Basic JS (variables, functions).
- **Week 3:** Install Cypress, write a simple test (e.g., login).
- **Week 4:** Add assertions + practice on a demo site.
- **Month 2:** Learn APIs + custom commands.
- **Month 3:** Git basics + intermediate JS (optional).

---

## 5. Example: Putting It Together

Here’s a test using core skills:

```javascript
describe('Login Tests', () => {
  it('logs in successfully', () => {
    cy.visit('https://the-internet.herokuapp.com/login');
    cy.get('#username').type('tomsmith');        // HTML + JS
    cy.get('#password').type('SuperSecretPassword!');
    cy.get('button').click();                    // Interaction
    cy.get('.flash.success').should('be.visible'); // Assertion + QA
  });
});
```

---

## 6. Why These Skills Matter

- **Cypress-Specific:** JS, HTML/CSS, and web app knowledge let you write and debug tests.
- **QA Career:** API, Git, and soft skills prep you for jobs (e.g., Cyprus fintech QA roles).
- **Beginner-Friendly:** Start with the core, grow into the rest.

---

## 7. What’s Your Next Step?
Want help with a specific skill (e.g., JS basics) or a sample test to practice? Let me know!

