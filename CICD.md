# What is Agile?
#### 1.Understand the Need
- Which application user wants to create.
  
#### 2.Create Product Backlog
- List of features (user stories) prioritized (e.g., search, place order).

#### 3.Start Sprint (2 Weeks)
- Team picks top stories to build (e.g., "search", "place order").

#### 4. Daily Standups
- 10–15 min check-in: what was done, what's next, blockers.

#### 5.Build & Test Continuously
- Code + automated tests = fewer bugs early.

#### 6.Sprint Review (Demo)
- Show working app to stakeholders (e.g., user can place an order).

#### 7.Sprint Retrospective -
- Reflect on what went well and what to improve.

#### 8.Next Sprint Begins -
- New features + user feedback (e.g., "order tracking", "live chat").

# Agile without CICD -
## 1] Manual Testing Slows Agile Down -
- Manual testers need hours or days to test every feature even if code is compeleted faster.
- Repetitive work: Same tests are done again and again for each sprint
- Human errors:	Testers can forget steps or miss bugs
- Delayed feedback:	Developers get feedback too late to fix quickly
### Solutions -
- JUnit, pytest, Mocha, TestNG
-	Jenkins, CircleCI
  
## 2] Frequent Delivery Can Fail Without Automation -
- Human errors:	Developer forgets a file or command.
- Too many step:	Developers must repeat the same steps by memory.
- Inconsistent setups: Dev, test, and prod environments behave differently.
- No rollback plan: If something fails, recovery is hard and slow.
### Solutions -
- Jenkin

## 3] Hard to Track Quality Without CI Tools
- Time-consuming: Testers or developers must manually run tests every time a change is made.
- Incomplete tests: Manual testing might miss edge cases, leading to bugs slipping through.
- Human errors	Testers can forget important steps or make mistakes.
- Lack of immediate feedback:	Developers might not know about bugs until later, even after the feature is already live.
### Solution -


## 4] Agile Teams Can Be Blocked by Environment Issues
- Inconsistent environments:	Devs test on their laptops, but the code fails on someone else's machine.
- Manual setup takes time:	Developers must manually install dependencies or configure services before they can work.
- Environment drift:	A change in one environment (like a new version of a library) could break something unexpectedly.
- Multiple steps to sync environments:	Developers must coordinate with others to make sure everyone’s environments are the same.
### Solution -
- Docker, Kubernetes

## 5] Incomplete Feedback Loop
- Manual deployment delays:	Even if a feature is ready, it can’t be tested by users until it’s manually deployed to production.
- Bugs discovered too late:	A feature works fine in testing but has issues in the real world that weren’t caught earlier.
- Slow user feedback:	Without continuous deployment, you can’t get real-time user input to fix problems faster.
- Not sure if users like the change:	It takes days or weeks to know if users are using or enjoying the feature.

# What is CICD ?
- CI/CD stands for:
  - CI → Continuous Integration
  - CD → Continuous Delivery / Continuous Deployment
- It is a modern software development practice that helps teams deliver code changes more frequently, reliably, and automatically.

## 1. Continuous Integration (CI) -
- Developers frequently (e.g., daily or several times per day) push their code to a shared version control system like Git.
- Each commit triggers an automated build and test process.

#### Steps -
- Commit Code to GitHub
  - Developer pushes code to a shared GitHub repository.

- CI Tool Detects Push
  - Jenkins/GitLab CI is triggered automatically via webhook.

- Pull Latest Code
  - CI tool clones or updates the code from the repository.

- Run Build
  - Installs dependencies and compiles or packages the code.

- Run Automated Tests
  - Executes unit tests, integration tests, and linters.

- Report Results
  - Sends success/failure notifications to developers.
 
## 2. Continuous Delivery/Deployment -
- CI Passes – Code is built and tested.
- Package Code – Create artifact (e.g., Docker image, .jar).
- Deploy to Staging – Automatically deploy to pre-production.
- Test in Staging – Run integration/E2E tests.
- Manual Approval – Team reviews and approves.
- Deploy to Production – Manually trigger final release.

![image](https://github.com/user-attachments/assets/e0f26630-fc25-41a0-b71b-8b529bf5be24)







