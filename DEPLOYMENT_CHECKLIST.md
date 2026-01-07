# 🚀 Deployment Checklist

## Before Deployment

### ✅ Code Preparation
- [x] API keys moved to environment variables
- [x] `.env` file created and added to `.gitignore`
- [x] Debug mode disabled for production
- [x] `requirements.txt` updated with all dependencies
- [x] Production server configured (Gunicorn)
- [x] Security configurations added

### ✅ Files Created
- [x] `.env` - Environment variables (DO NOT COMMIT)
- [x] `.env.example` - Template for environment variables
- [x] `.gitignore` - Ignore sensitive files
- [x] `requirements.txt` - Python dependencies
- [x] `Procfile` - Process file for deployment
- [x] `runtime.txt` - Python version specification
- [x] `render.yaml` - Render deployment configuration
- [x] `DEPLOYMENT.md` - Deployment instructions
- [x] `README.md` - Project documentation

## Deployment Steps

### 1. Local Testing
- [ ] Test app locally: `python app.py`
- [ ] Verify all forms work
- [ ] Test voice transcription
- [ ] Test text chat
- [ ] Check for console errors

### 2. Git Setup
```bash
# Initialize git (if not already done)
git init

# Add all files
git add .

# Commit
git commit -m "Initial commit - Ready for deployment"

# Create GitHub repo and push
git remote add origin YOUR_GITHUB_REPO_URL
git branch -M main
git push -u origin main
```

### 3. Render Setup
- [ ] Sign up at https://render.com
- [ ] Click "New +" → "Web Service"
- [ ] Connect GitHub account
- [ ] Select your repository
- [ ] Configure service:
  - Name: `banking-form-assistant`
  - Environment: `Python 3`
  - Build Command: `pip install -r requirements.txt`
  - Start Command: `gunicorn app:app`
  - Plan: `Free`

### 4. Environment Variables
Add these in Render Dashboard → Environment:

```
GEMINI_API_KEY = [Your Gemini API Key]
OPENROUTER_API_KEY = [Your OpenRouter API Key]
SECRET_KEY = [Generate random string]
FLASK_ENV = production
```

To generate SECRET_KEY:
```bash
python -c "import os; print(os.urandom(24).hex())"
```

### 5. Deploy
- [ ] Click "Create Web Service"
- [ ] Wait 2-5 minutes for deployment
- [ ] Check deploy logs for errors
- [ ] Visit your live URL

### 6. Post-Deployment Testing
- [ ] Open deployed URL
- [ ] Test home page loads
- [ ] Test form selection
- [ ] Test voice input
- [ ] Test text chat
- [ ] Complete full form submission
- [ ] Check Render logs for errors

## API Keys

### Get Gemini API Key:
1. Visit: https://makersuite.google.com/app/apikey
2. Sign in with Google
3. Click "Create API Key"
4. Copy the key

### Get OpenRouter API Key:
1. Visit: https://openrouter.ai/keys
2. Sign up/Login
3. Click "Create Key"
4. Copy the key

## Troubleshooting

### Build Fails
- [ ] Check `requirements.txt` is correct
- [ ] Verify Python version in `runtime.txt`
- [ ] Review build logs in Render

### App Won't Start
- [ ] Verify environment variables are set
- [ ] Check start command is correct
- [ ] Review Render logs
- [ ] Ensure PORT binding is correct

### API Errors
- [ ] Verify API keys are correct
- [ ] Check API rate limits
- [ ] Review error logs
- [ ] Test APIs individually

### Performance Issues
- [ ] Free tier has cold starts (30-60s)
- [ ] Consider upgrading to paid tier
- [ ] Optimize API calls
- [ ] Add caching if needed

## Security Checklist

- [x] No hardcoded API keys in code
- [x] `.env` file in `.gitignore`
- [x] Debug mode disabled in production
- [x] Secret key properly configured
- [ ] HTTPS enabled (automatic on Render)
- [ ] API keys rotated regularly
- [ ] Error messages don't expose sensitive info

## Monitoring

### After Deployment:
- [ ] Set up error notifications in Render
- [ ] Monitor API usage
- [ ] Check application logs regularly
- [ ] Monitor Render free tier hours (750/month)

### Render Dashboard:
- View logs: Dashboard → Your Service → Logs
- Check metrics: Dashboard → Your Service → Metrics
- Restart service: Dashboard → Your Service → Manual Deploy

## Maintenance

### Regular Tasks:
- [ ] Review and rotate API keys monthly
- [ ] Check API usage and costs
- [ ] Update dependencies: `pip list --outdated`
- [ ] Monitor error logs
- [ ] Backup important data

### Updates:
```bash
# Make changes locally
git add .
git commit -m "Your update message"
git push origin main
# Render auto-deploys
```

## Support Resources

- **Render Docs**: https://render.com/docs
- **Gemini API**: https://ai.google.dev/docs
- **OpenRouter**: https://openrouter.ai/docs
- **Flask**: https://flask.palletsprojects.com/

## Emergency Contacts

If something breaks:
1. Check Render logs first
2. Review recent commits
3. Roll back if needed: `git revert HEAD`
4. Check API status pages
5. Review error messages carefully

---

## ✅ Ready to Deploy?

Make sure you have:
- [x] All code changes committed
- [x] GitHub repository created
- [x] Render account set up
- [x] API keys ready
- [x] Read DEPLOYMENT.md

**You're all set! Follow the steps above to deploy your app.**

Good luck! 🚀
