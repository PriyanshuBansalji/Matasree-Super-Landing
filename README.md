# Matasree Super - Landing Page

A beautiful, responsive landing page for **matasreesuper.com** - your ultimate online supermarket launching in April 2026.

## Features

✨ **Responsive Design** - Works perfectly on desktop, tablet, and mobile devices  
🎨 **Modern UI** - Clean and professional design with smooth animations  
📧 **Contact Form** - Integrated contact form with email notifications  
🔗 **Easy Deployment** - Simple setup and deployment options  
⚡ **Fast Loading** - Lightweight and optimized for performance  

## Project Structure

```
matasree-landing/
├── index.html           # Main landing page
├── assets/
│   ├── styles.css      # Styling and responsive design
│   └── script.js       # Contact form and interactions
└── README.md           # This file
```

## Quick Start

### Option 1: Open Locally (No Server Required)

Simply open `index.html` in your web browser and navigate through the page. The contact form will show a message prompting setup.

```bash
# Windows
start index.html

# macOS
open index.html

# Linux
xdg-open index.html
```

### Option 2: Run with a Local Server

#### Python 3
```bash
python -m http.server 8000
```

#### Node.js (http-server)
```bash
npm install -g http-server
http-server
```

#### Using Python 2
```bash
python -m SimpleHTTPServer 8000
```

Then open: `http://localhost:8000`

## Deployment Options

### 1. **Vercel** (Recommended - Free & Fast)

```bash
# Install Vercel CLI
npm install -g vercel

# Deploy
vercel
```

### 2. **Netlify**

```bash
# Install Netlify CLI
npm install -g netlify-cli

# Deploy
netlify deploy --prod --dir=.
```

### 3. **GitHub Pages**

1. Create a GitHub repository: `matasreesuper.github.io`
2. Push the entire `matasree-landing` folder to `main` branch
3. The site will be live at: `https://matasreesuper.github.io`

### 4. **Traditional Web Hosting**

Upload all files to your hosting provider via FTP/cPanel:
- `index.html`
- `assets/styles.css`
- `assets/script.js`

## Email Integration Setup

The contact form is ready to send emails. Choose one of these methods:

### **Method 1: Using FormSubmit.co** (Free, No Backend Needed)

1. Open `index.html` and find this line in the form:
   ```html
   <form class="contact-form" id="contactForm">
   ```

2. Replace the form submission to use FormSubmit.co:
   ```html
   <form action="https://formsubmit.co/your-email@example.com" method="POST">
       <input type="hidden" name="_captcha" value="false">
       <input type="hidden" name="_next" value="https://matasreesuper.com">
       <!-- form fields -->
   </form>
   ```

3. Update `assets/script.js` to remove the custom form handler (or keep it commented).

### **Method 2: Using Backend with Node.js**

1. Update the backend endpoint in `assets/script.js`:
   ```javascript
   const response = await fetch('http://your-backend.com/api/contact', {
       method: 'POST',
       headers: {
           'Content-Type': 'application/json',
       },
       body: JSON.stringify({ name, email, message }),
   });
   ```

2. In your backend (Node.js + Nodemailer example):
   ```javascript
   const nodemailer = require('nodemailer');

   const transporter = nodemailer.createTransport({
       service: 'gmail',
       auth: {
           user: 'your-email@gmail.com',
           pass: 'your-app-password'  // Use App Password, not real password
       }
   });

   app.post('/api/contact', async (req, res) => {
       const { name, email, message } = req.body;
       
       const mailOptions = {
           from: 'your-email@gmail.com',
           to: 'info@matasreesuper.com',
           subject: `New Contact Form Submission from ${name}`,
           text: `Name: ${name}\nEmail: ${email}\n\nMessage:\n${message}`
       };

       try {
           await transporter.sendMail(mailOptions);
           res.json({ message: 'Email sent successfully' });
       } catch (error) {
           res.status(500).json({ message: 'Failed to send email' });
       }
   });
   ```

3. **For Gmail**, create an App Password:
   - Enable 2-factor authentication
   - Go to: https://myaccount.google.com/apppasswords
   - Generate a new app password for "Mail"
   - Use this password in the code above

### **Method 3: Using AWS SES** (Production-Ready)

```javascript
const AWS = require('aws-sdk');
const ses = new AWS.SES({ region: 'us-east-1' });

app.post('/api/contact', async (req, res) => {
    const { name, email, message } = req.body;
    
    const params = {
        Source: 'noreply@matasreesuper.com',
        Destination: {
            ToAddresses: ['info@matasreesuper.com']
        },
        Message: {
            Subject: {
                Data: `New Contact from ${name}`
            },
            Body: {
                Text: {
                    Data: `Name: ${name}\nEmail: ${email}\n\n${message}`
                }
            }
        }
    };

    try {
        await ses.sendEmail(params).promise();
        res.json({ message: 'Email sent successfully' });
    } catch (error) {
        res.status(500).json({ message: 'Failed to send email' });
    }
});
```

## Customization Guide

### Change Colors
Edit `assets/styles.css` - Look for CSS variables at the top:
```css
:root {
    --primary-color: #ff6b35;       /* Orange */
    --secondary-color: #004e89;     /* Dark Blue */
    --accent-color: #1e9b18;        /* Green */
}
```

### Update Contact Email
Edit `assets/script.js` - Update the endpoint or email address in the form submission handler.

### Add Your Logo
Replace the "Logo Coming Soon 🎨" text in `index.html` with:
```html
<img src="assets/logo.png" alt="Matasree Super Logo" class="logo-img">
```

Then add to your `assets/` folder your logo image.

### Update Social Links
In `index.html`, update the footer social links:
```html
<a href="https://facebook.com/matasreesuper" class="social-link">Facebook</a>
<a href="https://twitter.com/matasreesuper" class="social-link">Twitter</a>
<a href="https://instagram.com/matasreesuper" class="social-link">Instagram</a>
```

## Domain Configuration

### Connect matasreesuper.com

**For Vercel:**
```bash
vercel env add VERCEL_ENV production
# Add custom domain in Vercel dashboard
```

**For Netlify:**
1. Go to Site Settings → Domain Management
2. Add custom domain: `matasreesuper.com`
3. Update DNS records

**For GitHub Pages:**
Create a `CNAME` file in the root with:
```
matasreesuper.com
```

**For Traditional Hosting:**
Update DNS records to point to your hosting provider's nameservers.

## SEO & Meta Tags

To improve search engine visibility, update `index.html` meta tags:

```html
<meta name="description" content="Matasree Super - Your trusted online supermarket launching in April 2026. Wide selection, fast delivery, and secure payments.">
<meta name="keywords" content="online supermarket, grocery delivery, shopping, matasree">
<meta name="author" content="Matasree Super">
<meta property="og:title" content="Matasree Super - Coming Soon">
<meta property="og:description" content="Your ultimate shopping destination launching in April 2026">
<meta property="og:image" content="https://matasreesuper.com/assets/og-image.png">
```

## Performance Tips

1. **Optimize Images** - Use WebP format for logos and banners
2. **Enable Caching** - Set cache headers on Vercel/Netlify
3. **Minify CSS/JS** - Use tools like UglifyJS for production
4. **Use CDN** - Cloudflare free tier provides global CDN

## Browser Support

✅ Chrome (latest)  
✅ Firefox (latest)  
✅ Safari (latest)  
✅ Edge (latest)  
✅ Mobile browsers  

## Troubleshooting

### Contact form not sending emails?
- Check browser console (F12) for errors
- Verify CORS settings if using external API
- Test with hardcoded email first

### Page not responsive?
- Clear browser cache (Ctrl+Shift+Delete)
- Check viewport meta tag is present
- Test in incognito/private mode

### Performance issues?
- Compress images before uploading
- Reduce JavaScript bundle size
- Enable gzip compression on server

## Future Enhancements

- [ ] Newsletter signup integration
- [ ] Product showcase section
- [ ] Interactive countdown timer
- [ ] Live chat widget
- [ ] Blog section
- [ ] User testimonials

## Support

For questions or issues, contact: **info@matasreesuper.com**

---

**Last Updated:** March 2026  
**Status:** Ready for Production  
**Domain:** matasreesuper.com
#   M a t a s r e e - S u p e r  
 #   M a t a s r e e - S u p e r  
 #   M a t a s r e e - S u p e r - L a n d i n g  
 