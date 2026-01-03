# Security Policy

## 🔐 Protecting API Keys and Sensitive Data

### Critical Security Rules

**🚨 NEVER commit API keys or secrets to version control!**

This repository uses Google Gemini API keys. Follow these rules to keep your credentials secure:

### ✅ DO:
- Store API keys in the `.env` file (which is gitignored)
- Use environment variables for all sensitive credentials
- Keep `.env` in your `.gitignore` file
- Use `.env.example` as a template (with placeholder values only)
- Rotate API keys regularly (every 90 days recommended)
- Monitor your API usage for unexpected activity

### ❌ DON'T:
- **NEVER** put API keys in `config.json`
- **NEVER** put API keys in any Python files
- **NEVER** put API keys in documentation files
- **NEVER** commit `.env` file to git
- **NEVER** share API keys in public forums, chat, or email
- **NEVER** hardcode credentials anywhere in the codebase

## 🚨 If You Accidentally Expose an API Key

If you accidentally commit an API key to the repository:

1. **Immediately revoke the compromised key:**
   - Go to [Google AI Studio](https://makersuite.google.com/app/apikey)
   - Delete the exposed API key
   - Generate a new one

2. **Remove the key from git history:**
   ```bash
   # Option 1: Using git-filter-repo (recommended)
   git filter-repo --path config.json --invert-paths --force
   
   # Option 2: Using BFG Repo-Cleaner
   bfg --replace-text passwords.txt
   ```

3. **Force push to update remote:**
   ```bash
   git push --force --all
   ```

4. **Update your local `.env` with the new key**

5. **Never reuse the compromised key**

## 📋 Security Checklist

Before committing code, verify:

- [ ] No API keys in any tracked files
- [ ] `.env` file is in `.gitignore`
- [ ] No hardcoded credentials in Python files
- [ ] No sensitive data in JSON configuration files
- [ ] No API keys in documentation or README files
- [ ] Only placeholder values (like `YOUR_KEY_HERE`) in examples

## 🔍 How to Check for Exposed Secrets

Run these commands before committing:

```bash
# Check for potential API key patterns
git diff | grep -i "api.key\|apikey\|api_key"

# Check staged files
git diff --cached | grep -E "AIza[0-9A-Za-z_-]{35}"

# Verify .env is not staged
git status | grep ".env"
```

## 🛡️ Additional Security Best Practices

1. **Use GitHub Secret Scanning:**
   - GitHub automatically scans for exposed secrets
   - Enable push protection in repository settings
   - Review and act on any alerts immediately

2. **Principle of Least Privilege:**
   - Use API keys with minimal required permissions
   - Create separate keys for development and production

3. **Secure Local Development:**
   - Don't share `.env` files via email or chat
   - Use secure password managers for storing keys
   - Don't commit `.env.local`, `.env.production`, etc.

4. **Regular Audits:**
   - Review git history for accidentally committed secrets
   - Check API usage dashboards regularly
   - Update dependencies to patch vulnerabilities

## 📞 Reporting Security Issues

If you discover a security vulnerability in this repository:

1. **Do NOT** open a public issue
2. Contact the repository owner directly
3. Provide details about the vulnerability
4. Allow time for the issue to be addressed before public disclosure

## 🔗 Resources

- [Google AI Studio API Keys](https://makersuite.google.com/app/apikey)
- [GitHub Secret Scanning](https://docs.github.com/en/code-security/secret-scanning)
- [git-filter-repo](https://github.com/newren/git-filter-repo)
- [BFG Repo-Cleaner](https://rtyley.github.io/bfg-repo-cleaner/)

---

**Remember: Security is everyone's responsibility. When in doubt, don't commit it!**
