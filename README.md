# Cypress Cheat Sheet for QA Freshers

## 1. Setup & Basics

### What is Cypress?
A tool to test web apps by simulating user actions (e.g., clicking, typing) and checking results.

### Install:
```bash
mkdir my-cypress-project
cd my-cypress-project
npm init -y
npm install cypress --save-dev
npx cypress open
```

### Run Tests:
- **GUI:** `npx cypress open` (interactive Test Runner).
- **Terminal:** `npx cypress run` (headless mode).

### File Setup:
- **Tests:** `cypress/e2e/my_test.cy.js`
- **Commands:** `cypress/support/commands.js`

---

## 2. Test Structure

### Basic Template:
```javascript
describe('My Web App Tests', () => {        // Group related tests
  beforeEach(() => {                        // Runs before each test
    cy.visit('https://example.com')         // Start at this URL
  })

  it('does a thing', () => {                // One test case
    // Test steps here
  })
})
```

### Explanation:
- `describe`: Organizes tests (e.g., "Login Tests").
- `it`: A single test (e.g., "logs in successfully").
- `beforeEach`: Sets up a fresh state.

---

## 3. Navigation & Interaction

### Visit a Page:
```javascript
cy.visit('/login')                    // Relative URL
cy.visit('https://example.com')       // Full URL
```

### Type Text:
```javascript
cy.get('#username').type('testuser')  // Find input by ID, type text
cy.get('input[name="pass"]').type('123') // By attribute
```

### Click:
```javascript
cy.get('button').click()              // Click a button
cy.get('.submit-btn').click()         // By class
```

### Select Dropdown:
```javascript
cy.get('#dropdown').select('Option 2') // Choose from <select>
```

---

## 4. Assertions

### Check Text:
```javascript
cy.get('.header').should('have.text', 'Welcome') // Exact text
cy.get('.msg').should('contain', 'Success')      // Partial text
```

### Visibility:
```javascript
cy.get('.error').should('be.visible')           // Is it shown?
cy.get('.popup').should('not.be.visible')       // Is it hidden?
```

### Count Elements:
```javascript
cy.get('li').should('have.length', 3)          // Exactly 3 items
cy.get('tr').should('have.length.gte', 2)      // 2 or more
```

### URL Check:
```javascript
cy.url().should('eq', 'https://example.com/dashboard') // Exact URL
cy.url().should('include', '/dashboard')              // Partial URL
```

---

## 5. Waiting & Handling Time

Cypress **automatically waits** for elements.

### Explicit Wait:
```javascript
cy.wait(2000)                         // Wait 2 seconds (rarely needed)
cy.get('.loader', { timeout: 10000 }) // Wait up to 10s for element
```

### Wait for Action:
```javascript
cy.get('button').click()
cy.get('.result').should('be.visible') // Waits until result appears
```

---

## 6. Working with Forms

### Fill a Form:
```javascript
it('submits a login form', () => {
  cy.visit('/login')
  cy.get('#username').type('testuser')
  cy.get('#password').type('pass123')
  cy.get('#login-btn').click()
  cy.get('.welcome').should('contain', 'testuser')
})
```

### Clear Input:
```javascript
cy.get('#username').clear().type('newuser') // Clear then type
```

---

## 7. API Testing

### GET Request:
```javascript
it('checks API data', () => {
  cy.request('GET', 'https://api.example.com/users')
    .then((response) => {
      expect(response.status).to.eq(200)          // Check status
      expect(response.body).to.have.length(5)     // Check data length
    })
})
```

### POST Request:
```javascript
it('logs in via API', () => {
  cy.request({
    method: 'POST',
    url: '/api/login',
    body: { username: 'testuser', password: 'pass123' }
  }).its('body.token').should('exist') // Check token exists
})
```

---

## 8. Custom Commands

### Define (in `cypress/support/commands.js`):
```javascript
Cypress.Commands.add('login', (user, pass) => {
  cy.visit('/login')
  cy.get('#username').type(user)
  cy.get('#password').type(pass)
  cy.get('#login-btn').click()
})
```

### Use:
```javascript
it('uses custom login', () => {
  cy.login('testuser', 'pass123')
  cy.get('.dashboard').should('be.visible')
})
```

---

## 9. Debugging

### Log:
```javascript
cy.log('Starting login test')         // Print message in Test Runner
```

### Pause:
```javascript
cy.pause()                            // Pause test to inspect
```

### Inspect:
- Use `npx cypress open` to see each step live.
- Click steps in Test Runner to view DOM snapshots.

---

## 10. Real-World Example: Testing a Page

### Full Test Suite:
```javascript
describe('E-Commerce Checkout', () => {
  beforeEach(() => {
    cy.visit('https://example.com/shop')
  })

  it('adds item to cart', () => {
    cy.get('.product').first().click()
    cy.get('#add-to-cart').click()
    cy.get('.cart-count').should('have.text', '1')
  })

  it('fails checkout with empty cart', () => {
    cy.get('#checkout-btn').click()
    cy.get('.error').should('contain', 'Cart is empty')
  })

  it('checks cart API', () => {
    cy.request('GET', '/api/cart')
      .its('body.items')
      .should('be.empty')
  })
})
```

---

## 11. Tips for Beginners

- **Practice:** Use [The Internet](https://the-internet.herokuapp.com) for free testing pages.
- **Learn:**
  - JavaScript basics: `let x = 'hi'; console.log(x)`
  - HTML: `<button id="btn">Click</button>` → `cy.get('#btn')`
- **Common Tasks:**
  - Login tests
  - Form submissions
  - Table data checks: `cy.get('td').eq(0).should('contain', 'data')`

---

## 12. Quick Commands Reference

| Action           | Code Example                              | Purpose                  |
|-----------------|-----------------------------------------|--------------------------|
| Visit          | `cy.visit('/page')`                      | Open a page              |
| Type           | `cy.get('#id').type('text')`             | Enter text               |
| Click          | `cy.get('.class').click()`               | Click an element         |
| Assert Text    | `cy.get('.text').should('contain', 'x')` | Check text               |
| Assert Count   | `cy.get('li').should('have.length', 2)`  | Count elements           |
| API Call       | `cy.request('GET', '/api')`             | Test an API              |
| Custom Command | `cy.login('user', 'pass')`              | Reuse code               |

---

## 13. Your First Test

### Try this:
```javascript
it('tests a login failure', () => {
  cy.visit('https://the-internet.herokuapp.com/login')
  cy.get('#username').type('wrong')
  cy.get('#password').type('wrong')
  cy.get('button').click()
  cy.get('.flash.error').should('be.visible')
})
```

This covers setup, writing tests, assertions, APIs, and debugging—all the major topics to get you started with Cypress.  

Want to dive deeper into any section or test something specific? Let me know!
