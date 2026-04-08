# Turn Off AI Features - Deployment Guide

## Current Status
✅ Plugin version 0.0.4 deployed to WordPress.org
✅ Published and live at: https://wordpress.org/plugins/turn-off-ai-features/
✅ GitHub Actions workflow configured
✅ All code synchronized

## For Users
Install from WordPress.org plugin directory:
- Search for "Turn Off AI Features"
- Or visit: https://wordpress.org/plugins/turn-off-ai-features/

## For Developers - Deploying Future Versions

### Automatic Deployment (Recommended)
Once you configure GitHub Secrets (one-time setup):

```bash
# 1. Make your changes
# 2. Update version in turn-off-ai-features.php
# 3. Update Stable tag in readme.txt
# 4. Update Changelog in readme.txt
# 5. Commit and tag:

git add .
git commit -m "Release version 0.0.5"
git tag v0.0.5
git push origin main
git push origin v0.0.5

# GitHub Actions automatically deploys to WordPress.org
```

### Setup GitHub Secrets (Required for automatic deployment)

1. Get your WordPress.org SVN password:
   - Visit: https://wordpress.org/support/user/raftaar1191/edit/
   - Account & Security section
   - Create or find your SVN password

2. Add to GitHub:
   - Go to: https://github.com/acrosswp/turn-off-ai-features/settings/secrets/actions
   - Click "New repository secret"
   - Add: `SVN_USERNAME` = `raftaar1191`
   - Add: `SVN_PASSWORD` = [Your WordPress.org SVN password]

3. Done! Next tag push will auto-deploy.

### Manual Deployment (Backup method)

```bash
svn checkout https://plugins.svn.wordpress.org/turn-off-ai-features svn-repo
cd svn-repo
# Update trunk/ directory with new files
svn add trunk/*
svn commit trunk -m "Updated to version 0.0.5" --username raftaar1191
svn copy trunk tags/0.0.5 -m "Tag version 0.0.5" --username raftaar1191
```

## Workflow File
Location: `.github/workflows/wordpress-plugin-deploy.yml`

Automatically triggers on ANY tag push that matches the pattern `v*` (e.g., v0.0.5, v1.0.0)

## Support
- WordPress.org: https://wordpress.org/support/plugin/turn-off-ai-features/
- GitHub: https://github.com/acrosswp/turn-off-ai-features
