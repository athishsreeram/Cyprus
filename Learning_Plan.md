
# Must-Have Skills to Learn Cypress (QA Beginners)

## 1. Basic JavaScript Knowledge
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

## 2. HTML & CSS Fundamentals
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

## 3. Understanding Web Applications
**Why:** Cypress tests how users interact with web apps, so you need to know what’s happening on a page.

**What to Learn:**
- **Page Elements:** Buttons, forms, links, tables.
- **Browser Basics:** URL changes, page loads.
- **DevTools:** Inspect elements (right-click → Inspect in Chrome).

**Example:**
Inspect a login button to find its ID or class for `cy.get()`.

**How to Learn:** Play with a site like [The Internet](https://the-internet.herokuapp.com) and use browser DevTools (2-3 days).

---

## 4. Basic QA Concepts
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
