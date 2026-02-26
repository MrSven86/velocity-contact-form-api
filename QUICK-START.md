# QUICK START - 5 MINUTE SETUP

## What You're About to Do:
Upload these files to GitHub, then import to Vercel. That's it!

---

## STEP 1: Create GitHub Repo (2 minutes)

1. Go to: https://github.com/new
2. Repository name: `velocity-contact-form-api`
3. Keep it Public (or Private if you prefer)
4. **DO NOT** check "Add a README file"
5. Click "Create repository"

---

## STEP 2: Upload Files to GitHub (1 minute)

On the new repo page:

1. Click the link that says "uploading an existing file"
2. Drag ALL 4 files from the folder I gave you:
   - api/send-email.js
   - package.json
   - vercel.json
   - README.md
3. Scroll down and click "Commit changes"

**Note:** Make sure the `api` folder structure is preserved!

---

## STEP 3: Import to Vercel (1 minute)

1. Go back to your Vercel tab (the one you have open now)
2. Click "Continue with GitHub"
3. Authorize Vercel to access your repos
4. Find `velocity-contact-form-api` 
5. Click "Import"
6. Click "Deploy" (keep all default settings)

Wait 30 seconds... ✅ DEPLOYED!

---

## STEP 4: Add Your Resend API Key (1 minute)

1. After deployment, click "Go to Dashboard"
2. Click "Settings" tab at top
3. Click "Environment Variables" in sidebar
4. Click "Add New"
5. Name: `RESEND_API_KEY`
6. Value: `re_E3NSUWRc...` (from resend.com/api-keys - your existing key)
7. Click "Save"

**Important:** Now you need to redeploy!
- Go to "Deployments" tab
- Click the three dots (...) on the latest deployment
- Click "Redeploy"
- Wait 30 seconds

---

## STEP 5: Get Your URL

After redeployment:
1. Copy the URL shown (like `https://velocity-contact-form-api-xyz.vercel.app`)
2. Your endpoint is: `https://YOUR-URL.vercel.app/api/send-email`

---

## DONE! 🎉

Now go to your Lovable project and update the form to use this URL.

Total time: ~5 minutes
Total cost: $0
Will it ever pause? NOPE!

---

## Test It

Use this in your browser console or Postman:

```javascript
fetch('https://YOUR-URL.vercel.app/api/send-email', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({
    name: 'Test',
    email: 'test@test.com',
    message: 'Testing!'
  })
})
.then(r => r.json())
.then(d => console.log(d))
```

You should get an email! ✉️
