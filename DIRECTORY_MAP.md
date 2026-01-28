# Zulip Repository Directory Map 🗺️

**Quick visual guide to help you navigate the Zulip codebase.**

---

## 📂 Complete Directory Structure

```
zulip/
│
├── 🔧 CORE APPLICATION
│   ├── zerver/                    ⭐ BACKEND - Django application
│   │   ├── views/                 → API endpoints (REST API)
│   │   ├── models/                → Database models (User, Message, Channel, etc.)
│   │   ├── lib/                   → Utility functions and helpers
│   │   ├── actions/               → Business logic actions
│   │   ├── tests/                 → Backend test suite
│   │   ├── webhooks/              → 100+ external integrations
│   │   ├── tornado/               → Real-time event server
│   │   ├── management/            → Django management commands
│   │   ├── middleware/            → Request/response middleware
│   │   ├── context_processors/   → Template context
│   │   ├── forms.py               → Form validation
│   │   └── migrations/            → Database migrations
│   │
│   ├── web/                       ⭐ FRONTEND - Web application
│   │   ├── src/                   → TypeScript/JavaScript source
│   │   │   ├── *.ts               → Main app logic
│   │   │   ├── settings_*.ts     → Settings pages
│   │   │   ├── message_*.ts      → Message handling
│   │   │   └── compose*.ts       → Message composition
│   │   ├── templates/             → Handlebars templates
│   │   ├── tests/                 → Frontend unit tests
│   │   ├── styles/                → Symlink to static/styles/
│   │   ├── shared/                → Shared utilities
│   │   └── third/                 → Third-party code
│   │
│   ├── static/                    ⭐ STATIC ASSETS
│   │   ├── styles/                → All CSS files
│   │   ├── images/                → Image assets
│   │   ├── audio/                 → Sound files
│   │   ├── js/                    → Compiled JavaScript
│   │   ├── templates/             → Compiled templates
│   │   └── webpack-bundles/       → Webpack output
│   │
│   ├── templates/                 ⭐ HTML TEMPLATES
│   │   ├── zerver/                → Main app templates
│   │   │   ├── app/               → Main application UI
│   │   │   ├── emails/            → Email templates
│   │   │   ├── login.html         → Login page
│   │   │   └── register.html      → Registration
│   │   └── corporate/             → Corporate pages
│   │
│   └── zproject/                  ⭐ DJANGO CONFIGURATION
│       ├── settings.py            → Django settings
│       ├── urls.py                → URL routing
│       ├── backends.py            → Authentication backends
│       ├── dev_settings.py        → Development settings
│       └── prod_settings.py       → Production settings
│
├── 📚 DOCUMENTATION
│   ├── docs/                      ⭐ CONTRIBUTOR DOCS (185K words!)
│   │   ├── contributing/          → How to contribute
│   │   ├── development/           → Dev environment setup
│   │   ├── subsystems/            → Architecture deep-dives
│   │   ├── testing/               → Testing guides
│   │   ├── tutorials/             → Step-by-step tutorials
│   │   ├── production/            → Deployment guides
│   │   ├── documentation/         → Doc writing guide
│   │   └── overview/              → High-level overviews
│   │
│   ├── api_docs/                  → REST API documentation
│   │   ├── api_docs/              → API endpoint docs
│   │   └── changelog.md           → API changelog
│   │
│   ├── README.md                  → Main readme
│   ├── CONTRIBUTING.md            → Contribution guide
│   ├── CONTRIBUTOR_QUICK_START.md → Quick start (NEW!)
│   ├── FOCUS_AREAS.md             → Focus guide (NEW!)
│   └── CODE_OF_CONDUCT.md         → Community guidelines
│
├── 🔌 SPECIALIZED MODULES
│   ├── analytics/                 → Usage analytics and stats
│   ├── confirmation/              → Email confirmation system
│   ├── corporate/                 → Business/billing logic
│   ├── zilencer/                  → Server monitoring/licensing
│   └── starlight_help/            → Help center docs
│
├── 🛠️ DEVELOPMENT TOOLS
│   ├── tools/                     ⭐ DEV/BUILD SCRIPTS
│   │   ├── provision              → Initial setup script
│   │   ├── run-dev                → Start dev server
│   │   ├── test-backend           → Run backend tests
│   │   ├── test-js-with-node      → Run frontend tests
│   │   ├── test-all               → Run all tests
│   │   ├── lint                   → Run linters
│   │   ├── webpack                → Build frontend
│   │   └── [100+ other tools]     → Various utilities
│   │
│   ├── scripts/                   → Server management scripts
│   │   ├── upgrade-zulip          → Upgrade script
│   │   ├── restart-server         → Server restart
│   │   └── lib/                   → Script utilities
│   │
│   └── puppet/                    → Infrastructure config
│       ├── zulip/                 → Puppet modules
│       └── zulip_ops/             → Operations config
│
├── 🌍 INTERNATIONALIZATION
│   └── locale/                    → Translation files (.po)
│       ├── en/                    → English (source)
│       ├── de/                    → German
│       ├── es/                    → Spanish
│       └── [50+ languages]        → Other translations
│
├── ⚙️ CONFIGURATION FILES
│   ├── pyproject.toml             ⭐ Python config (dependencies, tools)
│   ├── package.json               ⭐ Node.js config (dependencies)
│   ├── pnpm-lock.yaml             → Package lock file
│   ├── tsconfig.json              → TypeScript configuration
│   ├── eslint.config.js           → ESLint rules
│   ├── prettier.config.js         → Code formatting
│   ├── stylelint.config.js        → CSS linting
│   ├── .gitignore                 → Git ignore rules
│   ├── .editorconfig              → Editor settings
│   ├── Dockerfile-postgresql      → PostgreSQL Docker
│   ├── Vagrantfile                → Vagrant config
│   └── manage.py                  → Django management
│
├── 🧪 TESTING
│   ├── puppeteer_tests/           → End-to-end browser tests
│   ├── zerver/tests/              → Backend unit tests
│   ├── web/tests/                 → Frontend unit tests
│   └── .github/workflows/         → CI/CD workflows
│
└── 📦 OTHER
    ├── patches/                   → Patches for dependencies
    ├── pgroonga/                  → PostgreSQL extension
    ├── version.py                 → Version info
    ├── uv.lock                    → Python lock file
    ├── LICENSE                    → Apache 2.0 license
    ├── SECURITY.md                → Security policy
    └── .vscode/                   → VSCode settings
```

---

## 🎯 Navigation Guide by Task

### "I want to add/modify an API endpoint"
```
zerver/views/          → Find or create your view
zerver/tests/          → Add tests
api_docs/              → Document the API
```

### "I want to change the UI"
```
web/src/               → TypeScript/JavaScript logic
web/templates/         → HTML templates
static/styles/         → CSS styling
web/tests/             → Add/update tests
```

### "I want to add a webhook integration"
```
zerver/webhooks/
└── myservice/
    ├── view.py        → Webhook handler
    ├── tests.py       → Test suite
    ├── fixtures/      → Test payloads
    └── doc.md         → Documentation
```

### "I want to change database schema"
```
zerver/models/         → Modify models
./manage.py makemigrations → Create migration
zerver/migrations/     → Migration files
zerver/tests/          → Update tests
```

### "I want to improve documentation"
```
docs/                  → Main documentation
api_docs/              → API documentation
README.md              → Main readme
CONTRIBUTING.md        → Contribution guide
```

### "I want to add tests"
```
zerver/tests/          → Backend tests
web/tests/             → Frontend tests
puppeteer_tests/       → E2E tests
```

---

## 📊 Directory Importance by Contribution Type

### Backend Developer Focus
| Priority | Directory | Purpose |
|----------|-----------|---------|
| 🔴 HIGH | `zerver/views/` | API endpoints |
| 🔴 HIGH | `zerver/models/` | Data models |
| 🔴 HIGH | `zerver/lib/` | Utilities |
| 🟡 MEDIUM | `zerver/actions/` | Business logic |
| 🟡 MEDIUM | `zerver/tests/` | Tests |
| 🟢 LOW | `zerver/tornado/` | Real-time (advanced) |

### Frontend Developer Focus
| Priority | Directory | Purpose |
|----------|-----------|---------|
| 🔴 HIGH | `web/src/` | Main logic |
| 🔴 HIGH | `web/templates/` | UI templates |
| 🔴 HIGH | `static/styles/` | CSS |
| 🟡 MEDIUM | `web/tests/` | Tests |
| 🟡 MEDIUM | `templates/zerver/` | Django templates |
| 🟢 LOW | `web/shared/` | Shared utils |

### Integration Developer Focus
| Priority | Directory | Purpose |
|----------|-----------|---------|
| 🔴 HIGH | `zerver/webhooks/` | All integrations |
| 🟡 MEDIUM | `api_docs/` | Integration docs |
| 🟢 LOW | `zerver/lib/` | Helper functions |

### Documentation Writer Focus
| Priority | Directory | Purpose |
|----------|-----------|---------|
| 🔴 HIGH | `docs/contributing/` | Contributor guides |
| 🔴 HIGH | `docs/subsystems/` | Architecture |
| 🟡 MEDIUM | `api_docs/` | API docs |
| 🟡 MEDIUM | `README.md` | Main readme |
| 🟢 LOW | `docs/production/` | Deployment |

---

## 🚦 File Type Quick Reference

### Python Files
- `*.py` - Python source code
- `zerver/views/*.py` - API endpoints (JSON responses)
- `zerver/models/*.py` - Database models (Django ORM)
- `zerver/tests/*.py` - Backend tests (pytest)

### JavaScript/TypeScript Files
- `*.ts` - TypeScript source
- `*.js` - JavaScript source
- `web/src/*.ts` - Frontend application logic
- `web/tests/*.test.js` - Frontend unit tests
- `puppeteer_tests/*.ts` - E2E tests

### Template Files
- `*.hbs` - Handlebars templates (frontend)
- `*.html` - Django/Jinja2 templates (backend)
- `web/templates/*.hbs` - Client-side templates
- `templates/zerver/*.html` - Server-side templates

### Style Files
- `*.css` - Cascading Style Sheets
- `static/styles/*.css` - All application styles
- `static/styles/app_*.css` - Component-specific styles

### Configuration Files
- `*.json` - JSON config files
- `*.yaml` / `*.yml` - YAML config files
- `*.toml` - TOML config files (Python)
- `*.config.js` - JavaScript config

---

## 🔍 Finding Files Quickly

### By Feature
```bash
# Find files related to messages
find . -name "*message*" -type f

# Find files related to settings
find . -name "*settings*" -type f

# Find all TypeScript files
find . -name "*.ts" -type f
```

### By Type
```bash
# All Python test files
find . -name "test_*.py"

# All API views
ls zerver/views/

# All webhooks
ls zerver/webhooks/

# All CSS files
find static/styles -name "*.css"
```

### By Content
```bash
# Search for a function
grep -r "def send_message" zerver/

# Search for an API endpoint
grep -r "/api/v1/messages" .

# Search for a CSS class
grep -r "message-row" static/styles/
```

---

## 💡 Pro Tips

### Starting Points for Common Tasks

| Task | Start Here |
|------|-----------|
| Add API endpoint | Copy similar file from `zerver/views/` |
| Add UI feature | Look at `web/src/` + `web/templates/` |
| Add webhook | Copy `zerver/webhooks/helloworld/` |
| Fix CSS | Search `static/styles/` for the class |
| Add test | Find similar test in `zerver/tests/` or `web/tests/` |
| Update docs | Edit relevant file in `docs/` |

### Understanding Code Flow

**Backend Request Flow:**
```
URL (zproject/urls.py)
  ↓
View (zerver/views/*.py)
  ↓
Action (zerver/actions/*.py)
  ↓
Model (zerver/models/*.py)
  ↓
Database (PostgreSQL)
```

**Frontend Event Flow:**
```
User Action (web/templates/*.hbs)
  ↓
Event Handler (web/src/*.ts)
  ↓
API Call (web/src/channel.ts)
  ↓
Backend API (zerver/views/*.py)
  ↓
Real-time Update (zerver/tornado/)
  ↓
Frontend Update (web/src/*.ts)
```

---

## 📁 Critical Files You Should Know

### Configuration
- `pyproject.toml` - Python dependencies and tool config
- `package.json` - Node.js dependencies
- `zproject/settings.py` - Django settings
- `tsconfig.json` - TypeScript config

### Entry Points
- `manage.py` - Django management (backend)
- `tools/run-dev` - Development server launcher
- `web/src/main.ts` - Frontend entry point

### Testing
- `tools/test-backend` - Backend test runner
- `tools/test-js-with-node` - Frontend test runner
- `tools/lint` - Linter runner

### Documentation
- `docs/index.md` - Documentation index
- `docs/subsystems/index.md` - Architecture index
- `api_docs/index.md` - API documentation index

---

## 🎓 Learning Path Through Directories

### Week 1: Exploration
1. Browse `zerver/views/` - See API endpoints
2. Browse `web/src/` - See frontend code
3. Browse `zerver/models/` - Understand data models
4. Read `docs/subsystems/` - Architecture

### Week 2: Understanding
1. Pick one feature area (e.g., messages)
2. Trace code from `zerver/views/messages.py`
3. To `web/src/message_*.ts`
4. Read related tests

### Week 3: Contributing
1. Find `good first issue`
2. Locate relevant files
3. Make changes
4. Add tests
5. Submit PR

---

## ✅ Directory Navigation Checklist

- [ ] I know where API endpoints are: `zerver/views/`
- [ ] I know where frontend code is: `web/src/`
- [ ] I know where tests go: `zerver/tests/` and `web/tests/`
- [ ] I know where to find docs: `docs/`
- [ ] I know where integrations are: `zerver/webhooks/`
- [ ] I can find the file I need to edit
- [ ] I know how to run tests for my changes

---

**You now have a map! Navigate with confidence! 🧭**
