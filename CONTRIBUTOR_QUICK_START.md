# Zulip Contributor Quick Start Guide 🚀

This guide helps you focus on the **essential areas** of the Zulip repository so you can start contributing effectively without getting overwhelmed by the codebase.

## 📋 Table of Contents
1. [What is Zulip?](#what-is-zulip)
2. [Repository Overview](#repository-overview)
3. [Focus Areas for Contributors](#focus-areas-for-contributors)
4. [Development Setup](#development-setup)
5. [Testing & Linting](#testing--linting)
6. [Contribution Workflow](#contribution-workflow)
7. [Quick Reference](#quick-reference)

---

## What is Zulip?

Zulip is an **open-source organized team chat application** with unique topic-based threading. It's used by Fortune 500 companies and leading open-source projects like Rust.

**Key Stats:**
- 1,500+ contributors
- 185K+ words of documentation
- 100% Mypy type coverage
- 500+ commits merged monthly

---

## Repository Overview

### Core Architecture

```
┌─────────────┐     ┌──────────────┐     ┌─────────────┐
│   Frontend  │────▶│    Django    │────▶│  PostgreSQL │
│  (TypeScript)│     │   Backend    │     │  Database   │
└─────────────┘     └──────────────┘     └─────────────┘
                           │
                    ┌──────┴──────┐
                    │   Tornado   │
                    │  Real-time  │
                    │   Server    │
                    └─────────────┘
```

### Technology Stack

| Layer | Technologies |
|-------|-------------|
| **Backend** | Python 3.10+, Django 5.2, Tornado |
| **Frontend** | TypeScript, JavaScript, Webpack, Handlebars |
| **Database** | PostgreSQL, Redis |
| **Queue** | Celery for async tasks |
| **Testing** | pytest, Puppeteer, Node test runners |
| **Code Quality** | Mypy (100%), Ruff, ESLint, Prettier |

---

## Focus Areas for Contributors

### 🎯 Top-Level Directories (What You Need to Know)

#### **Essential Directories** - Start Here!

| Directory | Purpose | When to Work Here |
|-----------|---------|-------------------|
| **`zerver/`** | Core Django backend | Adding API endpoints, models, business logic |
| **`web/`** | Frontend application | UI features, TypeScript/JavaScript work |
| **`docs/`** | Documentation | Improving contributor guides |
| **`templates/`** | HTML templates | UI templates and email templates |
| **`static/`** | Static assets | CSS, images, fonts |

#### **Feature-Specific Directories**

| Directory | Purpose | When to Work Here |
|-----------|---------|-------------------|
| **`zerver/webhooks/`** | 100+ integrations | Adding new webhook integrations |
| **`zerver/views/`** | API endpoints | Creating/modifying REST APIs |
| **`zerver/models/`** | Database models | Schema changes, model logic |
| **`zerver/tornado/`** | Real-time server | WebSocket, push notifications |
| **`api_docs/`** | API documentation | Documenting REST API |
| **`analytics/`** | Usage analytics | Analytics features |

#### **Configuration & Tools**

| Directory | Purpose | When to Work Here |
|-----------|---------|-------------------|
| **`zproject/`** | Django settings | Configuration, URL routing |
| **`tools/`** | Dev/build scripts | Development tooling |
| **`scripts/`** | Server management | Deployment, upgrade scripts |

#### **Optional/Advanced**

| Directory | Purpose |
|-----------|---------|
| **`corporate/`** | Business/billing logic |
| **`puppet/`** | Infrastructure config |
| **`locale/`** | i18n translations |
| **`zilencer/`** | Server monitoring |
| **`confirmation/`** | Email confirmations |

### 🔍 Common Contribution Types

#### 1. **Backend Development** (Python/Django)
**Focus on:**
- `zerver/views/` - API endpoints
- `zerver/models/` - Data models
- `zerver/lib/` - Utility libraries
- `zerver/tests/` - Backend tests

**Example Issues:** "Add API endpoint for...", "Fix bug in..."

#### 2. **Frontend Development** (TypeScript/JavaScript)
**Focus on:**
- `web/src/` - Frontend application code
- `web/templates/` - Handlebars templates
- `web/tests/` - Frontend tests
- `static/styles/` - CSS/styling

**Example Issues:** "Improve UI for...", "Add frontend feature..."

#### 3. **Webhook Integrations**
**Focus on:**
- `zerver/webhooks/<integration>/` - Integration code
- `zerver/webhooks/<integration>/tests/` - Tests
- `api_docs/` - Integration docs

**Example Issues:** "Add integration for Jira/GitHub/..."

#### 4. **Documentation**
**Focus on:**
- `docs/contributing/` - Contributor guides
- `docs/subsystems/` - Architecture docs
- `api_docs/` - API documentation
- `README.md`, `CONTRIBUTING.md` - Main docs

**Example Issues:** "Improve documentation for..."

#### 5. **Testing & Quality**
**Focus on:**
- `zerver/tests/` - Backend tests
- `web/tests/` - Frontend tests
- `.github/workflows/` - CI/CD

**Example Issues:** "Add test coverage for...", "Fix flaky test..."

---

## Development Setup

### Quick Start Commands

```bash
# 1. Clone the repository
git clone https://github.com/zulip/zulip.git
cd zulip

# 2. Set up development environment
./tools/provision

# 3. Start development server
./tools/run-dev

# 4. Access Zulip at http://localhost:9991
```

### Key Development Tools

| Command | Purpose |
|---------|---------|
| `./tools/provision` | Set up development environment |
| `./tools/run-dev` | Start development server |
| `./tools/test-backend` | Run backend tests |
| `./tools/test-js-with-node` | Run frontend tests |
| `./tools/lint` | Run all linters |
| `./manage.py dbshell` | Access PostgreSQL shell |

---

## Testing & Linting

### Running Tests

```bash
# Backend tests (Python)
./tools/test-backend zerver/tests/test_<feature>.py

# Frontend tests (JavaScript/TypeScript)
./tools/test-js-with-node web/tests/<feature>.test.js

# Full test suite
./tools/test-all

# End-to-end tests
./tools/test-puppeteer
```

### Linting

```bash
# Run all linters
./tools/lint

# Specific linters
./tools/lint --backend  # Python code (Ruff, Mypy)
./tools/lint --frontend # JavaScript/TypeScript (ESLint)
./tools/lint --templates # Template files

# Auto-fix what's possible
./tools/lint --fix
```

### Code Quality Standards

✅ **Requirements:**
- 100% Mypy type coverage (Python)
- All linters must pass
- All tests must pass
- Code must follow existing patterns

---

## Contribution Workflow

### Step-by-Step Process

1. **Find an Issue**
   - Look for `good first issue` or `help wanted` labels
   - Check [Zulip's GitHub issues](https://github.com/zulip/zulip/issues)

2. **Set Up Development Environment**
   ```bash
   ./tools/provision
   ./tools/run-dev
   ```

3. **Create a Branch**
   ```bash
   git checkout -b fix-issue-12345
   ```

4. **Make Changes**
   - Follow existing code patterns
   - Add/update tests
   - Update documentation if needed

5. **Test Your Changes**
   ```bash
   ./tools/test-backend <test-file>
   ./tools/lint --fix
   ```

6. **Commit Changes**
   ```bash
   git add .
   git commit -m "settings: Fix typo in email settings.
   
   Fixes #12345."
   ```

7. **Push and Create PR**
   ```bash
   git push origin fix-issue-12345
   ```
   Then create a Pull Request on GitHub.

8. **Address Review Feedback**
   - Respond to reviewer comments
   - Make requested changes
   - Push updates to the same branch

---

## Quick Reference

### 📚 Essential Documentation

| Resource | Link | Purpose |
|----------|------|---------|
| **Contributing Guide** | `CONTRIBUTING.md` | Complete contribution guide |
| **Development Docs** | `docs/development/` | Setup, environment, workflow |
| **Subsystems Guide** | `docs/subsystems/` | Architecture deep-dives |
| **Testing Guide** | `docs/testing/` | Testing practices |
| **API Docs** | `api_docs/` | REST API reference |

### 🔗 Important Links

- **Development Community:** https://zulip.com/development-community/
- **Documentation:** https://zulip.readthedocs.io/
- **Issue Tracker:** https://github.com/zulip/zulip/issues
- **Code of Conduct:** `CODE_OF_CONDUCT.md`

### 📁 Key Configuration Files

| File | Purpose |
|------|---------|
| `pyproject.toml` | Python dependencies, Mypy/Ruff config |
| `package.json` | Node.js dependencies |
| `tsconfig.json` | TypeScript configuration |
| `eslint.config.js` | ESLint rules |
| `prettier.config.js` | Code formatting rules |
| `manage.py` | Django management commands |

### 🎓 Learning Path

**New to Zulip?** Follow this order:

1. Read `README.md` - Understand what Zulip is
2. Read `CONTRIBUTING.md` - Learn how to contribute
3. Set up development environment - `./tools/provision`
4. Pick a `good first issue`
5. Read `docs/contributing/` - Detailed guides
6. Read relevant subsystem docs in `docs/subsystems/`
7. Make your first contribution!

### 💡 Pro Tips

✅ **Do:**
- Read existing code in the area you're working on
- Follow existing patterns and conventions
- Write tests for your changes
- Ask questions in the development community
- Start with small, focused changes

❌ **Don't:**
- Skip reading the documentation
- Make large, sweeping changes in your first PR
- Work on multiple unrelated issues in one PR
- Ignore linter/test failures
- Use AI to generate code without understanding it

---

## Getting Help

**Stuck?** Here's where to go:

1. **Documentation:** Check `docs/` directory first
2. **Common Questions:** See `CONTRIBUTING.md` FAQ section
3. **Development Community:** https://zulip.com/development-community/
4. **GitHub Issues:** Comment on the issue you're working on

**Before Asking:**
- Search existing documentation
- Check if your question was already answered
- Provide context and what you've already tried

---

## Summary: What to Focus On

### For Your First Contribution:

1. **Read:** `README.md` → `CONTRIBUTING.md`
2. **Setup:** Run `./tools/provision` and `./tools/run-dev`
3. **Explore:** Look at files in your area of interest
4. **Find:** Pick a `good first issue`
5. **Code:** Make minimal, focused changes
6. **Test:** Run `./tools/lint` and relevant tests
7. **Submit:** Create a pull request

### Key Directories by Contribution Type:

- **Backend API:** `zerver/views/`, `zerver/models/`, `zerver/lib/`
- **Frontend:** `web/src/`, `static/styles/`
- **Integrations:** `zerver/webhooks/`
- **Documentation:** `docs/`, `api_docs/`
- **Tests:** `zerver/tests/`, `web/tests/`

### Most Important:

📖 **Read the documentation** - Zulip has 185K+ words written specifically for contributors like you!

🎯 **Start small** - Focus on one area, one issue, one change at a time.

🤝 **Engage with the community** - Join the development chat, ask questions, learn from others.

---

**Welcome to Zulip! We're excited to have you contribute! 🎉**
