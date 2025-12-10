# Frappe Repo Template

A GitHub template repository that automatically initializes a new Frappe application with standardized configurations and best practices.

## ✨ Features

- 🚀 **Automatic App Initialization** - Creates a Frappe app using `bench new-app` on repo creation
- 📁 **Standardized Structure** - Includes pre-configured workflows, docs, and configs from `frappe-standard-template`
- 🤖 **Bot-Powered** - Uses GitHub App for secure, automated operations
- 🔄 **Always Up-to-Date** - Uses latest Frappe boilerplate from `bench new-app`
- ⚡ **Zero Manual Setup** - Just create repo from template and wait

## 🚀 Quick Start

### 1. Create New Repository

1. Click **"Use this template"** button above
2. Enter repository name (e.g., `student-portal`, `fee-management`)
3. Click **"Create repository"**

### 2. Wait for Initialization

The workflow automatically:
- Runs `bench new-app` with your repo name
- Copies standardized configs from `frappe-standard-template`
- Commits and pushes the initialized app

⏱️ **Takes ~3-5 minutes**

### 3. Check Progress

1. Go to **Actions** tab in your new repo
2. Watch the "Initialize Frappe App" workflow
3. Once complete, your app is ready!

## 📁 Generated Structure

After initialization, your repo will have:
```
your-repo/
├── your_repo/                      # App module (from bench new-app)
│   ├── __init__.py
│   ├── hooks.py
│   ├── modules.txt
│   ├── patches.txt
│   ├── templates/
│   ├── public/
│   └── your_repo/
│       └── __init__.py
├── .github/                        # From frappe-standard-template
│   ├── workflows/
│   │   └── (CI/CD workflows)
│   ├── ISSUE_TEMPLATE/
│   └── PULL_REQUEST_TEMPLATE.md
├── docs/                           # From frappe-standard-template
├── .pre-commit-config.yaml         # From frappe-standard-template
├── .releaserc                      # From frappe-standard-template
├── commitlint.config.js            # From frappe-standard-template
├── pyproject.toml                  # From bench new-app
├── license.txt                     # MIT License
└── README.md                       # From bench new-app
```

## 📝 Naming Convention

| Repository Name | App Name | App Title |
|-----------------|----------|-----------|
| `student-portal` | `student_portal` | `Student Portal` |
| `fee-management` | `fee_management` | `Fee Management` |
| `lms-badges` | `lms_badges` | `Lms Badges` |
| `MyCustomApp` | `mycustomapp` | `Mycustomapp` |

**Rules:**
- Repository name is converted to `snake_case` for app name
- Hyphens (`-`) become underscores (`_`)
- All lowercase for app name
- Title Case for app title

## 🔧 Using the Generated App

### Install in Your Bench
```bash
# Clone the app
bench get-app git@github.com:dhwani-ris/your-repo-name.git

# Install on site
bench --site yoursite.localhost install-app your_app_name

# Run migrations (if any)
bench --site yoursite.localhost migrate
```

### Development Workflow
```bash
# Create feature branch
git checkout -b feature/your-feature

# Make changes...

# Commit (follows commitlint conventions)
git commit -m "feat: add new doctype for student records"

# Push and create PR
git push origin feature/your-feature
```

## ⚙️ Configuration

### App Details (Auto-Generated)

| Property | Value |
|----------|-------|
| **Publisher** | DHWANI RIS |
| **Email** | frappeteam@dhwaniris.com |
| **License** | MIT |
| **Frappe Branch** | version-15 |
| **Default Branch** | develop |

### Modify Defaults

To change default values, edit the workflow file before creating repos:
```yaml
# In .github/workflows/init-frappe-app.yml

expect "App Publisher*"
send "Your Company Name\r"

expect "App Email*"
send "your-email@company.com\r"
```

## 🤖 GitHub App Setup

This template uses a GitHub App for authentication. If you're setting this up for a new organization:

### 1. Create GitHub App

1. Go to: `https://github.com/organizations/YOUR-ORG/settings/apps`
2. Click **"New GitHub App"**
3. Configure:
   - **Name:** `your-org-release-bot`
   - **Permissions:**
     - Contents: Read & Write
     - Metadata: Read-only
     - Workflows: Read & Write
   - **Installation:** Only on this account
4. Create and note the **App ID**
5. Generate **Private Key** (downloads `.pem` file)

### 2. Install App

1. Go to App settings → **Install App**
2. Install on your organization
3. Select **All repositories**

### 3. Add Secrets

Add these organization secrets:

| Secret Name | Value |
|-------------|-------|
| `DHWANI_RELEASE_BOT_APP_ID` | Your App ID |
| `DHWANI_RELEASE_BOT_PRIVATE_KEY` | Contents of `.pem` file |

## 🔍 Troubleshooting

### Workflow Not Running

**Check:**
- Is this a new repo created from template?
- Is this the first push to main/master?
- Does the app folder already exist? (skip condition)

### Permission Denied

**Check:**
- Is the GitHub App installed on the repo?
- Are organization secrets configured?
- Does the App have correct permissions?

### Clone Template Failed

**Check:**
- Is `frappe-standard-template` accessible to the GitHub App?
- Is the App installed on `frappe-standard-template` repo?

### App Already Initialized

The workflow skips if an app folder already exists. To re-initialize:

1. Delete the app folder manually
2. Re-run the workflow from Actions tab

## 📚 Related Resources

- [Frappe Framework Documentation](https://frappeframework.com/docs)
- [Frappe Standard Template](https://github.com/dhwani-ris/frappe-standard-template)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [Semantic Release](https://semantic-release.gitbook.io/)

## 🤝 Contributing

1. Fork the repository
2. Create feature branch: `git checkout -b feature/improvement`
3. Commit changes: `git commit -m "feat: add new feature"`
4. Push: `git push origin feature/improvement`
5. Open Pull Request

## 📄 License

MIT License - see [LICENSE](license.txt) for details.

---

**Maintained by DHWANI RIS Frappe Team** | frappeteam@dhwaniris.com
