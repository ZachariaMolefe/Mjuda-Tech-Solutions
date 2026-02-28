# EmailJS Setup Guide for Contact Form

The contact form is now set up to send emails using EmailJS. Follow these steps to make it work:

## Step 1: Create a Free EmailJS Account
1. Go to [emailjs.com](https://www.emailjs.com)
2. Click **Sign Up** and create a free account
3. Verify your email

## Step 2: Add Your Email Service
1. In the dashboard, go to **Email Services**
2. Click **Add New Service**
3. Select **Gmail** (or your preferred email provider)
4. Choose **Connect with Gmail** and authorize
5. Give it a name (e.g., "Gmail")
6. **Copy your Service ID** (looks like: `service_abc123xyz`)

## Step 3: Create an Email Template
1. Go to **Email Templates** in the dashboard
2. Click **Create New Template**
3. Add this template:

**Template Name:** Contact Form Email

**From Name:** `{{from_name}}`

**From Email:** `{{from_email}}`

**To Email:** `{{to_email}}`

**Subject:** `New Contact: {{subject}}`

**Content (HTML):**
```html
<h2>New Contact Form Submission</h2>
<p><strong>Name:</strong> {{from_name}}</p>
<p><strong>Email:</strong> {{from_email}}</p>
<p><strong>Phone:</strong> {{phone_number}}</p>
<p><strong>Subject:</strong> {{subject}}</p>
<p><strong>Message:</strong></p>
<p>{{message}}</p>
```

4. **Copy your Template ID** (looks like: `template_abc123xyz`)

## Step 4: Get Your Public Key
1. Go to **Account** settings
2. Find your **Public Key** (looks like: `abc123xyzPublicKey`)

## Step 5: Update Your Website Code
Open `script.js` in your text editor and update these lines with your actual IDs:

```javascript
// Line 1: Replace with your Public Key
emailjs.init('YOUR_PUBLIC_KEY_HERE');

// Line 2: Replace with your Service ID and Template ID
emailjs.send('YOUR_SERVICE_ID', 'YOUR_TEMPLATE_ID', {
```

**Example:**
```javascript
emailjs.init('1a2b3c4d5e6f7g8h9i0j');
emailjs.send('service_xyz123abc', 'template_abc123xyz', {
```

## Step 6: Update Email Address
Also in `script.js`, update your email address where it says:
```javascript
to_email: 'info@mjudatech.com',  // Change this to your actual email
```

Change to:
```javascript
to_email: 'mjuda@youremail.com',  // Your actual email address
```

## Step 7: Test It!
1. Go to your website's contact page
2. Fill out the form and click "Send Message"
3. You should receive an email at your inbox!

---

## Troubleshooting

**"Failed to send message" error:**
- Check that your Public Key, Service ID, and Template ID are correct
- Make sure your Gmail account has "Less secure apps" enabled (if using Gmail)
- Check the browser console (F12) for detailed error messages

**Not receiving emails:**
- Check your spam/junk folder
- Make sure your email address in step 6 is correct
- Verify your template variable names match exactly

**Need help?**
- EmailJS Documentation: https://www.emailjs.com/docs/
- Contact: support@emailjs.com
