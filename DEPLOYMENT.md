# Banking Form Assistant - Deployment Guide

## 🚀 Deploy to Render (Free Hosting)

### Prerequisites
- GitHub account
- Render account (sign up at https://render.com)
- Your API keys ready

### Step 1: Prepare Your Repository

1. **Create a `.env` file locally** (for local testing only):
   ```bash
   cp .env.example .env
   ```
   Then edit `.env` and add your actual API keys.

2. **Initialize Git and push to GitHub**:
   ```bash
   git init
   git add .
   git commit -m "Initial commit - Banking Form Assistant"
   git branch -M main
   git remote add origin YOUR_GITHUB_REPO_URL
   git push -u origin main
   ```

### Step 2: Deploy on Render

1. **Go to Render Dashboard**: https://dashboard.render.com/

2. **Create New Web Service**:
   - Click "New +" → "Web Service"
   - Connect your GitHub repository
   - Select the repository with your app

3. **Configure Service**:
   - **Name**: `banking-form-assistant` (or your choice)
   - **Region**: Choose closest to your users
   - **Branch**: `main`
   - **Runtime**: `Python 3`
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `gunicorn app:app`
   - **Plan**: `Free`

4. **Add Environment Variables**:
   Click "Advanced" → "Add Environment Variable":
   
   ```
   GEMINI_API_KEY = your_actual_gemini_api_key
   OPENROUTER_API_KEY = your_actual_openrouter_api_key
   SECRET_KEY = generate_a_random_string_here
   FLASK_ENV = production
   ```

5. **Deploy**: Click "Create Web Service"

6. **Wait for deployment** (takes 2-5 minutes)

7. **Your app will be live at**: `https://banking-form-assistant.onrender.com`

### Step 3: Get Your API Keys

#### Gemini API Key:
1. Go to https://makersuite.google.com/app/apikey
2. Sign in with Google account
3. Click "Create API Key"
4. Copy the key

#### OpenRouter API Key:
1. Go to https://openrouter.ai/keys
2. Sign up/Login
3. Click "Create Key"
4. Copy the key

### Step 4: Test Your Deployment

1. Visit your Render URL
2. Test the voice assistant
3. Try filling out a form
4. Check Render logs for any errors

### Important Notes

✅ **Security**: 
- Never commit `.env` file to Git
- Always use environment variables for API keys
- `.gitignore` is configured to prevent accidental commits

✅ **Free Tier Limitations**:
- Render free tier may sleep after 15 min of inactivity
- First request after sleep takes 30-60 seconds to wake up
- 750 hours/month free (enough for 1 service running 24/7)

✅ **Monitoring**:
- Check logs in Render dashboard
- Set up error notifications
- Monitor API usage to stay within free limits

### Troubleshooting

**App not starting?**
- Check Render logs for errors
- Verify all environment variables are set
- Ensure requirements.txt is complete

**API errors?**
- Verify API keys are correct
- Check API quotas haven't been exceeded
- Review OpenRouter and Gemini API dashboards

**Slow first load?**
- Normal for free tier (cold start)
- Consider upgrading to paid tier for always-on

### Local Development

```bash
# Install dependencies
pip install -r requirements.txt

# Copy environment file
cp .env.example .env
# Edit .env with your API keys

# Run locally
python app.py
# Visit http://localhost:5000
```

### Updating Your App

```bash
git add .
git commit -m "Your update message"
git push origin main
# Render will automatically redeploy
```

## Need Help?

- Render Docs: https://render.com/docs
- Gemini API Docs: https://ai.google.dev/docs
- OpenRouter Docs: https://openrouter.ai/docs

---

**Security Reminder**: Keep your API keys secret and never share them publicly!
