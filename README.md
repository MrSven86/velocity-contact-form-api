# Velocity Contact Form API

Simple serverless API for handling contact forms using Resend email service.

## What This Does

- Receives contact form submissions from your Lovable websites
- Sends formatted emails to your inbox via Resend
- No database needed
- Free on Vercel Hobby plan
- Never pauses or goes offline

## Files

- `api/send-email.js` - The serverless function that handles form submissions
- `package.json` - Dependencies (just Resend)
- `vercel.json` - Vercel configuration

## Setup Instructions

### 1. Create GitHub Repository

1. Go to https://github.com/new
2. Name: `velocity-contact-form-api`
3. Make it Public or Private (your choice)
4. Click "Create repository"

### 2. Upload These Files

1. Click "uploading an existing file"
2. Drag and drop all files (or upload one by one)
3. Commit the files

### 3. Deploy to Vercel

1. Go back to Vercel (vercel.com/new)
2. Click "Continue with GitHub"
3. Find your `velocity-contact-form-api` repo
4. Click "Import"
5. Click "Deploy"

### 4. Add Environment Variable

After deployment:
1. Go to Project Settings → Environment Variables
2. Add: `RESEND_API_KEY`
3. Value: Your Resend API key (from resend.com/api-keys)
4. Click "Save"
5. Redeploy (Settings → Deployments → Click the three dots → Redeploy)

### 5. Get Your API URL

After deployment, you'll get a URL like:
`https://velocity-contact-form-api.vercel.app`

Your endpoint will be:
`https://velocity-contact-form-api.vercel.app/api/send-email`

## Using in Lovable

In your Lovable contact form, update the submit handler:

```javascript
const handleSubmit = async (e) => {
  e.preventDefault();
  
  try {
    const response = await fetch('https://YOUR-VERCEL-URL.vercel.app/api/send-email', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({
        name: formData.name,
        email: formData.email,
        phone: formData.phone,
        message: formData.message,
        website: 'velocityweb.org' // Optional: which site sent this
      })
    });

    const data = await response.json();
    
    if (response.ok) {
      alert('Message sent successfully!');
      // Reset form or show success message
    } else {
      alert('Failed to send message: ' + data.error);
    }
  } catch (error) {
    console.error('Error:', error);
    alert('Error sending message. Please try again.');
  }
};
```

## Testing

You can test with curl:

```bash
curl -X POST https://YOUR-URL.vercel.app/api/send-email \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Test User",
    "email": "test@example.com",
    "phone": "123-456-7890",
    "message": "This is a test message"
  }'
```

## Cost

**$0** - Free forever on Vercel Hobby plan

Handles thousands of form submissions per month at no cost.
