# Zulip Focus Areas for Contributors 🎯

This guide helps you identify **exactly what to focus on** based on your interests and skills. Instead of being overwhelmed by the entire codebase, use this as your roadmap.

---

## 🗺️ Choose Your Path

Pick the area that matches your interests:

- [🔧 I want to work on Backend/API](#-backend--api-development)
- [🎨 I want to work on Frontend/UI](#-frontend--ui-development)
- [🔌 I want to add Integrations](#-integrations--webhooks)
- [📝 I want to improve Documentation](#-documentation)
- [🧪 I want to work on Testing](#-testing--quality-assurance)
- [🐛 I want to fix Bugs](#-bug-fixes)
- [🚀 I want to add Features](#-new-features)

---

## 🔧 Backend / API Development

### What You Need to Focus On

**Primary Directories:**
```
zerver/
├── views/          ← API endpoints (START HERE)
├── models/         ← Database models
├── lib/            ← Utility functions
├── actions/        ← Core business logic
└── tests/          ← Backend tests
```

### Essential Files to Understand

1. **API Endpoints:** `zerver/views/*.py`
   - Example: `zerver/views/messages.py` - Message sending APIs
   - Example: `zerver/views/users.py` - User management APIs

2. **Models:** `zerver/models/*.py`
   - `zerver/models/users.py` - User model
   - `zerver/models/messages.py` - Message model
   - `zerver/models/channels.py` - Channel model

3. **Authentication:** `zproject/backends.py`

### Common Backend Tasks

- Adding a new API endpoint
- Modifying database models
- Implementing business logic
- Adding server-side validation
- Optimizing database queries

### Getting Started

```bash
# 1. Find relevant view file
ls zerver/views/

# 2. Look at tests to understand behavior
ls zerver/tests/test_*.py

# 3. Run backend tests
./tools/test-backend zerver/tests/test_messages.py

# 4. Check API docs
cat api_docs/api_docs/openapi.yaml
```

### Key Documentation

- `docs/subsystems/schema-migrations.md` - Database changes
- `docs/subsystems/events-system.md` - Real-time events
- `docs/subsystems/queuing.md` - Background jobs
- `docs/tutorials/new-feature-tutorial.md` - Adding features

---

## 🎨 Frontend / UI Development

### What You Need to Focus On

**Primary Directories:**
```
web/
├── src/            ← TypeScript/JavaScript code (START HERE)
├── templates/      ← Handlebars templates
├── tests/          ← Frontend tests
└── styles/         ← CSS (in static/styles/)

static/
└── styles/         ← All CSS files
```

### Essential Files to Understand

1. **Main App:** `web/src/`
   - `web/src/message_list.ts` - Message list
   - `web/src/compose.ts` - Message composition
   - `web/src/settings_*.ts` - Settings pages

2. **Templates:** `web/templates/`
   - `web/templates/message_list.hbs` - Message display
   - `web/templates/compose.hbs` - Compose area

3. **Styles:** `static/styles/`
   - `static/styles/app_*.css` - Component styles

### Common Frontend Tasks

- Adding UI components
- Improving user interactions
- Fixing CSS/styling issues
- Adding client-side validation
- Implementing responsive design

### Getting Started

```bash
# 1. Look at TypeScript source
ls web/src/

# 2. Find templates
ls web/templates/

# 3. Run frontend tests
./tools/test-js-with-node web/tests/message_list.test.js

# 4. Check for linting issues
./tools/lint --frontend
```

### Key Documentation

- `docs/subsystems/front-end-build-process.md` - Build system
- `docs/subsystems/typescript.md` - TypeScript usage
- `docs/subsystems/html-css.md` - HTML/CSS guidelines
- `docs/subsystems/client.md` - Frontend architecture

---

## 🔌 Integrations / Webhooks

### What You Need to Focus On

**Primary Directory:**
```
zerver/webhooks/
├── github/         ← Example: GitHub integration
│   ├── view.py     ← Webhook handler
│   ├── tests.py    ← Tests
│   └── fixtures/   ← Test data
├── slack/          ← Example: Slack integration
└── [100+ others]
```

### Creating a New Integration

**Files You'll Create:**
```
zerver/webhooks/myservice/
├── __init__.py
├── view.py          ← Main webhook logic
├── tests.py         ← Test suite
├── fixtures/        ← Sample payloads
│   ├── event1.json
│   └── event2.json
└── doc.md           ← Documentation
```

### Essential Integration Patterns

1. **Simple Webhook:** `zerver/webhooks/helloworld/view.py`
2. **Complex Webhook:** `zerver/webhooks/github/view.py`
3. **Test Structure:** `zerver/webhooks/github/tests.py`

### Getting Started

```bash
# 1. Study existing integrations
ls zerver/webhooks/

# 2. Copy a similar integration as template
cp -r zerver/webhooks/helloworld zerver/webhooks/myservice

# 3. Run integration tests
./tools/test-backend zerver/webhooks/myservice/tests.py

# 4. Test locally
curl -X POST http://localhost:9991/api/v1/external/myservice \
  -d '{"test": "data"}'
```

### Key Documentation

- `docs/documentation/integrations.md` - Integration guide
- `zerver/webhooks/helloworld/` - Template to copy
- `api_docs/` - Integration documentation

---

## 📝 Documentation

### What You Need to Focus On

**Primary Directories:**
```
docs/
├── contributing/   ← Contributor guides (START HERE)
├── development/    ← Dev environment setup
├── subsystems/     ← Architecture deep-dives
├── testing/        ← Testing guides
└── tutorials/      ← Step-by-step tutorials

api_docs/           ← API documentation
README.md           ← Main readme
CONTRIBUTING.md     ← Contributing guide
```

### Common Documentation Tasks

- Improving clarity of existing docs
- Adding missing documentation
- Updating outdated information
- Creating tutorials
- Documenting new features

### Getting Started

```bash
# 1. Find docs to improve
ls docs/contributing/

# 2. Build docs locally
./tools/build-docs

# 3. View docs (opens in browser)
open docs/_build/html/index.html

# 4. Check for broken links
./tools/check-links
```

### Documentation Standards

- Use clear, simple language
- Include code examples
- Add screenshots where helpful
- Follow existing structure
- Test all code snippets

---

## 🧪 Testing / Quality Assurance

### What You Need to Focus On

**Test Directories:**
```
zerver/tests/       ← Backend tests
web/tests/          ← Frontend tests
puppeteer_tests/    ← End-to-end tests
```

### Types of Tests

1. **Backend Unit Tests:** `zerver/tests/test_*.py`
2. **Frontend Tests:** `web/tests/*.test.js`
3. **End-to-End Tests:** `puppeteer_tests/*.ts`
4. **Linters:** `./tools/lint`

### Getting Started

```bash
# 1. Run specific test file
./tools/test-backend zerver/tests/test_messages.py

# 2. Run frontend tests
./tools/test-js-with-node web/tests/compose.test.js

# 3. Run all linters
./tools/lint

# 4. Run end-to-end tests
./tools/test-puppeteer
```

### Key Documentation

- `docs/testing/testing.md` - Testing overview
- `docs/testing/testing-with-django.md` - Backend tests
- `docs/testing/testing-with-node.md` - Frontend tests

---

## 🐛 Bug Fixes

### Finding Bugs to Fix

**GitHub Labels:**
- `bug` - Confirmed bugs
- `good first issue` - Easy bugs for newcomers
- `help wanted` - Bugs needing attention

### Investigation Process

1. **Reproduce the Bug**
   ```bash
   ./tools/run-dev
   # Navigate to http://localhost:9991
   # Try to reproduce the issue
   ```

2. **Find Relevant Code**
   ```bash
   # Search for relevant keywords
   grep -r "error message" zerver/
   grep -r "function_name" web/src/
   ```

3. **Understand the Flow**
   - Read the code around the bug
   - Check related tests
   - Look at recent commits: `git log -- path/to/file.py`

4. **Fix and Test**
   ```bash
   # Make your fix
   # Add/update tests
   ./tools/test-backend <relevant-tests>
   ./tools/lint
   ```

---

## 🚀 New Features

### Before Starting

1. **Check if it's approved**
   - Look for label: `feature request`
   - Ensure maintainers approved it

2. **Understand the scope**
   - Read the issue description thoroughly
   - Check linked discussions
   - Ask clarifying questions if needed

### Feature Implementation Path

1. **Backend-First Approach:**
   ```
   Models → API → Tests → Frontend → UI Tests → Docs
   ```

2. **Frontend-First Approach:**
   ```
   UI Mockup → Template → Client Code → API → Backend → Tests
   ```

### Files You'll Touch

**Full-Stack Feature:**
- `zerver/models/*.py` - Data models
- `zerver/views/*.py` - API endpoints
- `zerver/tests/*.py` - Backend tests
- `web/src/*.ts` - Frontend logic
- `web/templates/*.hbs` - UI templates
- `static/styles/*.css` - Styling
- `docs/` - Documentation

---

## 📊 Contribution Complexity Matrix

### Easy (Good First Issues)

| Type | Example | Files to Touch |
|------|---------|----------------|
| Documentation | Fix typo | `docs/*.md` |
| UI Text | Update label | `templates/*.html` |
| Simple CSS | Fix alignment | `static/styles/*.css` |
| Add Test | Test coverage | `zerver/tests/*.py` |

### Moderate

| Type | Example | Files to Touch |
|------|---------|----------------|
| Bug Fix | Fix validation | `zerver/views/*.py` + tests |
| UI Feature | Add button | `web/src/*.ts` + template + CSS |
| Integration | Add webhook | `zerver/webhooks/new/` |
| API Enhancement | Add parameter | `zerver/views/*.py` + tests + docs |

### Complex

| Type | Example | Files to Touch |
|------|---------|----------------|
| Full Feature | New subsystem | Multiple dirs, many files |
| Refactoring | Rewrite component | Backend + frontend + tests |
| Performance | Optimize query | Models + views + caching |
| Security | Auth system | Backend + frontend + docs |

---

## 🎓 Recommended Learning Path

### Week 1: Setup & Exploration
- [ ] Read `README.md` and `CONTRIBUTING.md`
- [ ] Run `./tools/provision` and `./tools/run-dev`
- [ ] Browse key directories: `zerver/`, `web/src/`
- [ ] Run tests: `./tools/test-backend`, `./tools/test-js-with-node`
- [ ] Explore one subsystem in `docs/subsystems/`

### Week 2: First Contribution
- [ ] Find a `good first issue`
- [ ] Read code in that area
- [ ] Make your change
- [ ] Write/update tests
- [ ] Submit pull request

### Week 3+: Growing Skills
- [ ] Take on medium complexity issues
- [ ] Read more subsystem documentation
- [ ] Review others' pull requests
- [ ] Help answer questions in community

---

## 🔍 Quick Search Cheat Sheet

### Finding Specific Code

```bash
# Find where a function is defined
grep -r "def function_name" zerver/

# Find API endpoint
grep -r "api/v1/messages" zerver/

# Find frontend component
find web/src -name "*compose*"

# Find CSS class
grep -r "message-row" static/styles/

# Find template
find templates -name "*settings*"

# Find tests
find zerver/tests -name "*test_messages*"
```

### Understanding Dependencies

```bash
# Python dependencies
cat pyproject.toml

# JavaScript dependencies
cat package.json

# Check installed versions
./tools/python --version
node --version
```

---

## 💪 Essential Commands Cheat Sheet

```bash
# Development
./tools/provision              # Initial setup
./tools/run-dev                # Start dev server
./tools/run-dev --test         # Start with test data

# Testing
./tools/test-backend           # All backend tests
./tools/test-js-with-node      # All frontend tests
./tools/test-all               # Everything
./tools/lint                   # All linters
./tools/lint --fix             # Auto-fix issues

# Database
./manage.py dbshell            # PostgreSQL shell
./manage.py migrate            # Run migrations
./manage.py makemigrations     # Create migrations

# Debugging
./manage.py shell              # Django shell
./tools/run-dev --debug        # Debug mode
./tools/webpack                # Build frontend

# Cleanup
./tools/clean-all-caches       # Clear caches
./tools/destroy-all            # Reset everything
```

---

## ✅ Checklist: Am I Ready to Contribute?

Before starting your contribution:

- [ ] I've read `CONTRIBUTING.md`
- [ ] I can run `./tools/run-dev` successfully
- [ ] I can run tests with `./tools/test-backend`
- [ ] I understand the area I'm working on
- [ ] I've found the relevant code files
- [ ] I know which tests to run
- [ ] I've checked existing patterns in similar code
- [ ] I have a plan for my changes

---

## 🎯 Summary: Where to Focus

### Absolute Essentials (Read These!)
1. `README.md` - What is Zulip
2. `CONTRIBUTING.md` - How to contribute
3. `docs/contributing/` - Detailed guides
4. Relevant files in your contribution area

### By Contribution Type

| I want to... | Focus on... |
|--------------|-------------|
| **Write Python code** | `zerver/views/`, `zerver/models/`, `zerver/lib/` |
| **Write JavaScript/TypeScript** | `web/src/`, `web/templates/`, `static/styles/` |
| **Add integration** | `zerver/webhooks/`, copy `helloworld` example |
| **Fix documentation** | `docs/`, `README.md`, `api_docs/` |
| **Write tests** | `zerver/tests/`, `web/tests/` |
| **Fix a bug** | Find the bug, add test, fix code |

### Don't Worry About

- `puppet/` - Infrastructure (unless you're deploying)
- `corporate/` - Business logic (unless working on billing)
- `zilencer/` - Server monitoring (specialized)
- `locale/` - Translations (use Transifex)
- `scripts/` - Server scripts (unless deploying)

---

**You're ready! Pick your area and start contributing! 🚀**

Questions? Join the [Zulip development community](https://zulip.com/development-community/)!
