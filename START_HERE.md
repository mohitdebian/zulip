# 🎯 New Contributor? Start Here!

**Welcome to Zulip!** This page will help you get started contributing to the Zulip project quickly and effectively.

---

## 📖 Your Quick Start Path

Follow these steps in order:

### 1. Understand What Zulip Is (5 minutes)
- Read: [README.md](README.md)
- Visit: https://zulip.com

### 2. Learn How to Contribute (15 minutes)
- Read: [CONTRIBUTING.md](CONTRIBUTING.md) - Complete contribution guide
- Join: [Zulip Development Community](https://zulip.com/development-community/)

### 3. Get Oriented (10 minutes)
Choose ONE guide based on what you need:

| I want to... | Read this guide |
|--------------|-----------------|
| **Get a quick overview** | [CONTRIBUTOR_QUICK_START.md](CONTRIBUTOR_QUICK_START.md) |
| **Find what to work on** | [FOCUS_AREAS.md](FOCUS_AREAS.md) |
| **Navigate the codebase** | [DIRECTORY_MAP.md](DIRECTORY_MAP.md) |

### 4. Set Up Your Environment (30-60 minutes)
```bash
# Clone the repository
git clone https://github.com/zulip/zulip.git
cd zulip

# Set up development environment (downloads dependencies, sets up database)
./tools/provision

# Start the development server
./tools/run-dev

# Access Zulip at http://localhost:9991
```

### 5. Pick Your First Issue (10 minutes)
- Visit: https://github.com/zulip/zulip/issues
- Filter by: `label:good-first-issue`
- Comment on the issue to claim it

### 6. Make Your Contribution (varies)
- Make your changes
- Run tests: `./tools/test-backend` or `./tools/test-js-with-node`
- Run linters: `./tools/lint --fix`
- Commit and push
- Create a Pull Request on GitHub

---

## 🚀 Quick Reference Guides

### Overview & Getting Started
- **[CONTRIBUTOR_QUICK_START.md](CONTRIBUTOR_QUICK_START.md)** - Comprehensive quick start
  - Repository overview and architecture
  - Technology stack (Python/Django, TypeScript, PostgreSQL)
  - Development setup and workflow
  - Testing and linting guide
  - Common contribution types
  - Pro tips and best practices

### Focus on What Matters
- **[FOCUS_AREAS.md](FOCUS_AREAS.md)** - What to focus on by interest
  - Backend/API development paths
  - Frontend/UI development paths
  - Integration/webhook creation
  - Documentation improvements
  - Testing and quality assurance
  - Bug fixes and new features
  - Contribution complexity matrix

### Navigate the Codebase
- **[DIRECTORY_MAP.md](DIRECTORY_MAP.md)** - Visual directory structure
  - Complete directory tree with descriptions
  - Navigation guide by task
  - Priority levels by contribution type
  - File type reference
  - Quick search tips

---

## 📚 Essential Documentation

| Documentation | Purpose | When to Read |
|--------------|---------|--------------|
| [README.md](README.md) | Project overview | First thing |
| [CONTRIBUTING.md](CONTRIBUTING.md) | How to contribute | Before contributing |
| [CONTRIBUTOR_QUICK_START.md](CONTRIBUTOR_QUICK_START.md) | Quick start guide | When setting up |
| [FOCUS_AREAS.md](FOCUS_AREAS.md) | What to focus on | When choosing work |
| [DIRECTORY_MAP.md](DIRECTORY_MAP.md) | Navigate codebase | When finding files |
| [docs/](docs/) | 185K+ words of docs | As needed |

---

## 🎓 Learning Paths

### Beginner Path (First 1-2 weeks)
1. ✅ Read [README.md](README.md) and [CONTRIBUTING.md](CONTRIBUTING.md)
2. ✅ Read [CONTRIBUTOR_QUICK_START.md](CONTRIBUTOR_QUICK_START.md)
3. ✅ Set up development environment: `./tools/provision`
4. ✅ Browse [DIRECTORY_MAP.md](DIRECTORY_MAP.md)
5. ✅ Pick a `good first issue`
6. ✅ Make your first contribution
7. ✅ Get your first PR merged! 🎉

### Intermediate Path (Weeks 3-8)
1. Take on medium complexity issues
2. Read subsystem docs: `docs/subsystems/`
3. Explore different areas (backend, frontend, integrations)
4. Help review other contributors' PRs
5. Answer questions in the dev community

### Advanced Path (Months 2+)
1. Take on complex features
2. Deep dive into architecture
3. Mentor new contributors
4. Propose new features
5. Contribute to core systems

---

## 🔍 Find the Right Guide

### "I'm completely new to Zulip"
→ Start with [README.md](README.md), then [CONTRIBUTING.md](CONTRIBUTING.md)

### "I want a quick overview of everything"
→ Read [CONTRIBUTOR_QUICK_START.md](CONTRIBUTOR_QUICK_START.md)

### "I don't know what to work on"
→ Check [FOCUS_AREAS.md](FOCUS_AREAS.md) - find your path

### "I can't find the files I need"
→ Use [DIRECTORY_MAP.md](DIRECTORY_MAP.md) - visual guide

### "I want to understand the architecture"
→ Read `docs/subsystems/` - in-depth technical docs

### "I need help with testing/linting"
→ See [CONTRIBUTOR_QUICK_START.md](CONTRIBUTOR_QUICK_START.md#testing--linting)

### "I want to add a webhook"
→ See [FOCUS_AREAS.md](FOCUS_AREAS.md#-integrations--webhooks)

### "I'm stuck and need help"
→ Join [Zulip Development Community](https://zulip.com/development-community/)

---

## ⚡ Essential Commands

```bash
# Setup
./tools/provision              # Initial setup (run once)
./tools/run-dev                # Start dev server

# Development
./tools/test-backend           # Run backend tests
./tools/test-js-with-node      # Run frontend tests
./tools/lint                   # Run linters
./tools/lint --fix             # Auto-fix linting issues

# Database
./manage.py dbshell            # Access database
./manage.py migrate            # Run migrations

# Common workflows
./tools/test-backend zerver/tests/test_messages.py  # Test specific file
./tools/test-js-with-node web/tests/compose.test.js # Test specific file
```

---

## 🎯 Focus Areas Summary

### Backend Development
**Focus on:** `zerver/views/`, `zerver/models/`, `zerver/lib/`
**Learn:** Python, Django, PostgreSQL, REST APIs

### Frontend Development
**Focus on:** `web/src/`, `web/templates/`, `static/styles/`
**Learn:** TypeScript, JavaScript, HTML, CSS

### Integrations
**Focus on:** `zerver/webhooks/`
**Learn:** Webhook patterns, API integration

### Documentation
**Focus on:** `docs/`, `api_docs/`, `README.md`
**Learn:** Technical writing, Markdown

---

## 💡 Pro Tips

✅ **Do:**
- Start with small, focused changes
- Read existing code before modifying
- Follow existing patterns
- Write tests for your changes
- Ask questions in the dev community
- Read documentation thoroughly

❌ **Don't:**
- Skip the documentation
- Make large changes in your first PR
- Work on multiple issues in one PR
- Ignore linter/test failures
- Copy-paste code without understanding

---

## 🤝 Getting Help

1. **Read the docs first** - Most questions are answered in the documentation
2. **Search existing issues** - Someone may have asked before
3. **Join the dev community** - https://zulip.com/development-community/
4. **Be specific** - Provide context, what you tried, what happened
5. **Be patient** - Maintainers are volunteers

### Where to Ask

- **General questions:** Development community
- **Specific issues:** Comment on the GitHub issue
- **Bug reports:** Create a new issue
- **Feature ideas:** Discuss in community first

---

## 📊 By The Numbers

- **1,500+** contributors worldwide
- **185K+** words of documentation
- **100+** webhook integrations
- **100%** Mypy type coverage
- **500+** commits merged monthly

---

## 🎉 You're Ready!

You now have all the resources you need to start contributing to Zulip:

1. ✅ **Overview**: [CONTRIBUTOR_QUICK_START.md](CONTRIBUTOR_QUICK_START.md)
2. ✅ **Focus**: [FOCUS_AREAS.md](FOCUS_AREAS.md)
3. ✅ **Navigation**: [DIRECTORY_MAP.md](DIRECTORY_MAP.md)
4. ✅ **Environment**: `./tools/provision`
5. ✅ **First Issue**: https://github.com/zulip/zulip/issues?q=label:good-first-issue

**Pick your first issue and start coding!**

---

**Questions?** Join us at https://zulip.com/development-community/

**Ready to contribute?** Check out https://github.com/zulip/zulip/issues

**Want to learn more?** Read our full docs at https://zulip.readthedocs.io/
