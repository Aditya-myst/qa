# 📘 Complete Guide: SDLC, STLC, Bug Lifecycle & Automation Fundamentals

---

## 🔷 1. Software Development Life Cycle (SDLC)

The **Software Development Life Cycle (SDLC)** defines the complete process of building software—from idea to deployment.

### 🧭 Phases of SDLC

1. **Planning**

   * Define project scope, goals, timelines, and resources.
   * Identify risks and feasibility.
   * Output: Project Plan

2. **Requirements Analysis**

   * Gather and document business and technical requirements.
   * Types:

     * Functional Requirements (what the system should do)
     * Non-functional Requirements (performance, security, usability)
   * Output: SRS (Software Requirement Specification)

3. **Design**

   * Convert requirements into system architecture and design.
   * Types:

     * High-Level Design (HLD)
     * Low-Level Design (LLD)
   * Output: Design Documents

4. **Coding (Development)**

   * Developers write code based on design documents.
   * Follows coding standards and version control practices.

5. **Testing**

   * Validate the application against requirements.
   * Detect defects and ensure quality.

6. **Deployment**

   * Release the application to production.
   * Includes monitoring and maintenance.

---

## 🔶 2. Software Testing Life Cycle (STLC)

The **Software Testing Life Cycle (STLC)** focuses specifically on testing activities within SDLC.

### ⚙️ Phases of STLC

1. **Requirement Analysis**

   * Understand what needs to be tested.
   * Identify testable requirements.
   * Prepare RTM (Requirement Traceability Matrix)

2. **Test Planning**

   * Define testing strategy, scope, tools, timelines, and resources.
   * Output: Test Plan Document

   ✅ **Entry Criteria:**

   * Requirements available

   🚪 **Exit Criteria:**

   * Test Plan reviewed and approved

3. **Test Case Design**

   * Create detailed test cases and test data.
   * Review and optimize for coverage.

   ✅ Entry: Approved Test Plan
   🚪 Exit: Test Cases reviewed & signed off

4. **Test Environment Setup**

   * Configure hardware/software required for testing.
   * Includes servers, browsers, databases, tools.

   ⚠️ **Golden Rule:**

   > You cannot start Test Execution until the Test Environment is ready.
   > Because testing without an environment is like testing a car without a road.

5. **Test Execution**

   * Execute test cases.
   * Log defects for failures.

6. **Test Cycle Closure**

   * Evaluate testing outcomes.
   * Prepare Test Summary Report.
   * Identify lessons learned.

---

## 🚪 Entry & Exit Criteria (Quality Gates)

Each STLC phase has **entry and exit criteria** to maintain discipline and quality.

| Phase         | Entry Criteria     | Exit Criteria                  |
| ------------- | ------------------ | ------------------------------ |
| Test Planning | Requirements ready | Test Plan approved             |
| Test Design   | Test Plan ready    | Test cases reviewed            |
| Execution     | Environment ready  | Tests executed, defects logged |

👉 These act as **checkpoints** ensuring no phase is prematurely exited.

---

## 🐞 3. Bug (Defect) Lifecycle

A **bug lifecycle** describes the journey of a defect from discovery to closure.

### 🔄 Bug States

1. **NEW**

   * Tester finds a defect and logs it.

2. **ASSIGNED**

   * Bug is assigned to a developer.

3. **FIXED**

   * Developer resolves the issue.

4. **RE-TESTING**

   * Tester verifies the fix.

5. **CLOSED**

   * Bug is fixed and verified successfully.

---

### 🔁 Alternative Paths (Real-World Scenarios)

* **REOPENED**

  * Bug still exists after fix.

* **REJECTED**

  * Developer claims it's not a bug (expected behavior).

* **DEFERRED**

  * Bug is valid but postponed to a future release.

---

### ⚔️ The “Politics” of Bugs

* Developers may **reject bugs** due to:

  * Misunderstanding requirements
  * Edge cases not considered
* As a tester, you must:

  * Provide **clear steps to reproduce**
  * Attach **screenshots/videos/logs**
  * Reference **requirements**

👉 A well-documented bug is hard to reject.

---

## 🤖 4. Automation Engineering Fundamentals

Automation testing is not just clicking buttons—it's about interacting intelligently with the DOM.

---

### 🎯 Locators Strategy (WebdriverIO)

Locators identify elements in the UI.

#### 🥇 Priority Order

1. **ID**

   * Fastest and most reliable
   * Example:

     ```js
     $('#loginBtn')
     ```

2. **CSS Selectors**

   * Flexible and efficient
   * Example:

     ```js
     $('.btn.primary')
     ```

3. **XPath (Last Resort)**

   * Powerful but slow and brittle
   * Avoid unless necessary
   * Example:

     ```js
     $('//button[text()="Login"]')
     ```

---

### 🧱 Page Object Model (POM)

POM is a design pattern that separates:

* Test logic
* UI structure

#### ❌ Without POM

* UI change → Update 50 test scripts

#### ✅ With POM

* UI change → Update 1 file (e.g., `LoginPage.js`)

#### 📁 Example Structure

```
/pages
  LoginPage.js
/tests
  login.test.js
```

#### 📌 Example

```js
// LoginPage.js
class LoginPage {
  get loginButton() { return $('#loginBtn'); }

  clickLogin() {
    this.loginButton.click();
  }
}

module.exports = new LoginPage();
```

---

### ⏱️ Wait Strategies

Proper waits make automation **stable and reliable**.

#### ❌ Static Wait (Avoid)

```js
browser.pause(5000);
```

* Wastes time
* Causes flaky tests

#### ✅ Explicit Wait (Best Practice)

```js
$('#loginBtn').waitForClickable({ timeout: 10000 });
```

✔ Waits only until the condition is met
✔ Improves speed and stability

---

## 🧠 Key Takeaways

* SDLC defines **how software is built**
* STLC defines **how software is tested**
* Entry/Exit criteria ensure **process discipline**
* Bug lifecycle reflects **real-world collaboration challenges**
* Automation requires:

  * Smart locators
  * Clean architecture (POM)
  * Reliable waits

---
