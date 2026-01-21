# Plan: Publish Extension to VS Code Marketplace and Open VSX Registry

## Overview

Publish the Writer Color Theme extension to both the official VS Code Marketplace and the Open VSX Registry (for VSCodium users).

## Current State

The extension is well-prepared with most required metadata already in place:

- **Publisher ID**: `cboone` (already configured in `package.json`)
- **All required fields present**: name, displayName, description, version, license, repository, icon
- **Theme files ready**: Light and dark themes properly configured

**Missing pieces:**

- `.vscodeignore` file (to exclude unnecessary files from package)
- Publishing scripts in `package.json`
- `CHANGELOG.md` (recommended for marketplace)
- Account setup and access tokens
- CI/CD automation (optional but recommended)

---

## Phase 1: Prerequisites & Account Setup

### 1.1 VS Code Marketplace Setup

1. **Create Azure DevOps Organization** (if not exists)
   - Go to https://dev.azure.com
   - Sign in with Microsoft account
   - Create or select an organization

2. **Create Personal Access Token (PAT)**
   - Azure DevOps → User Settings → Personal Access Tokens
   - Create new token:
     - Organization: "All accessible organizations"
     - Scopes: Marketplace → Manage
     - Set expiration (recommend 1 year)
   - **Save token securely** (shown only once)

3. **Verify Publisher**
   - Go to https://marketplace.visualstudio.com/manage
   - Verify publisher `cboone` exists or create it
   - Login with vsce: `npx @vscode/vsce login cboone`

### 1.2 Open VSX Registry Setup

1. **Create Eclipse Account**
   - Register at https://accounts.eclipse.org
   - **Critical**: Set GitHub Username field to match your GitHub account

2. **Sign Publisher Agreement**
   - Log into https://open-vsx.org via GitHub
   - Authenticate with Eclipse account
   - Click "Show Publisher Agreement" on profile page and accept

3. **Generate Access Token**
   - Navigate to Access Tokens in settings
   - Create token with descriptive label (e.g., "writer-theme-local")
   - **Save token securely** (shown only once)

4. **Create Namespace**
   ```bash
   npx ovsx create-namespace cboone -p <token>
   ```

---

## Phase 2: Prepare Extension for Publishing

### 2.1 Create `.vscodeignore`

Create `.vscodeignore` in the repository root to exclude unnecessary files:

```
.git/
.github/
.yarn/
.pnp.cjs
.pnp.loader.mjs
.prettierignore
.gitignore
.DS_Store
docs/
markdown-samples/
screenshots/
node_modules/
*.vsix
yarn.lock
```

### 2.2 Create `CHANGELOG.md`

Create a changelog documenting version history:

```markdown
# Changelog

## [1.0.0] - YYYY-MM-DD

### Added
- Initial release
- Light theme (Writer Light)
- Dark theme (Writer Dark)
- Optimized for Markdown and long-form writing
```

### 2.3 Add Publishing Scripts to `package.json`

Add scripts section:

```json
{
  "scripts": {
    "package": "vsce package",
    "publish:vscode": "vsce publish",
    "publish:ovsx": "ovsx publish"
  }
}
```

### 2.4 Verify Package Contents

Test what will be included:

```bash
npx @vscode/vsce ls
```

---

## Phase 3: Manual Publishing (First Release)

### 3.1 Publish to VS Code Marketplace

```bash
# Login (one-time, caches credentials)
npx @vscode/vsce login cboone

# Package and publish
npx @vscode/vsce publish
```

Or package first, then upload manually:
```bash
npx @vscode/vsce package
# Upload .vsix at https://marketplace.visualstudio.com/manage
```

### 3.2 Publish to Open VSX Registry

```bash
# Package first (if not already done)
npx @vscode/vsce package

# Publish to Open VSX
npx ovsx publish writer-theme-vscode-1.0.0.vsix -p <token>
```

Or publish directly from source:
```bash
npx ovsx publish -p <token> --yarn
```

---

## Phase 4: Post-Publishing Verification

### 4.1 Verify VS Code Marketplace

1. Visit https://marketplace.visualstudio.com/items?itemName=cboone.writer-theme-vscode
2. Confirm icon, description, README render correctly
3. Install from VS Code to test

### 4.2 Verify Open VSX Registry

1. Visit https://open-vsx.org/extension/cboone/writer-theme-vscode
2. Confirm metadata matches
3. Install from VSCodium to test

---

## Files to Create/Modify

| File | Action | Purpose |
|------|--------|---------|
| `.vscodeignore` | Create | Exclude dev files from package |
| `CHANGELOG.md` | Create | Document version history |
| `package.json` | Modify | Add publishing scripts |

---

## Verification Checklist

- [ ] `.vscodeignore` excludes unnecessary files
- [ ] `npx @vscode/vsce ls` shows only required files
- [ ] Extension packages successfully (`npx @vscode/vsce package`)
- [ ] Published to VS Code Marketplace
- [ ] Published to Open VSX Registry
- [ ] Both marketplace pages display correctly
- [ ] Extension installs and works in VS Code
- [ ] Extension installs and works in VSCodium
