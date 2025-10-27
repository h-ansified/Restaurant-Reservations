markdown# Setup Guide

## Prerequisites

- Google account (for Sheets and Gmail)
- Make.com account (free tier works)
- Web hosting or ability to embed HTML
- Basic understanding of webhooks

## Step-by-Step Setup

### 1. Google Sheets Setup (5 minutes)

1. Go to [Google Sheets](https://sheets.google.com)
2. Create new spreadsheet
3. Name it "Restaurant Reservations" (or your preference)
4. Copy the spreadsheet ID from URL:
https://docs.google.com/spreadsheets/d/SPREADSHEET_ID/edit
5. Keep this ID for later

### 2. Make.com Account Setup (3 minutes)

1. Sign up at [make.com](https://make.com)
2. Verify your email
3. Complete basic setup

### 3. Import Make.com Blueprint (10 minutes)

1. Download `make-blueprint.json` from this repository
2. In Make.com, click **Scenarios** in left menu
3. Click **Create a new scenario**
4. Click the three dots (⋯) → **Import Blueprint**
5. Upload the downloaded JSON file
6. Click **Save**

### 4. Configure Make.com Connections (15 minutes)

#### A. Webhook Configuration
1. Click on Module 1 (Custom WebHook)
2. Make.com auto-generates a webhook URL
3. **COPY THIS URL** - you'll need it for the form
4. Example: `https://hook.eu2.make.com/xxxxxxxxxxxxx`

#### B. Google Sheets Connection
1. Click on Module 3 (List Sheets)
2. Click **Add** next to Connection
3. Sign in with your Google account
4. Grant permissions
5. Paste your Spreadsheet ID
6. Test connection
7. Repeat for Modules 5, 6, 7 (they'll use same connection)

#### C. Gmail Connection
1. Click on Module 9 (Send Email)
2. Click **Add** next to Connection
3. Sign in with Gmail account
4. Grant permissions
5. Test by sending yourself an email
6. Repeat for Module 10

### 5. Customize Email Template (10 minutes)

In Modules 9 and 10, replace the email content:
Current: {{1.name}}{{1.email}}{{1.phone}}...
Replace with:
Dear {{1.name}},
Thank you for your reservation!
Reservation Details:
📅 Date: {{1.date}}
🕐 Time: {{1.time}}
👥 Party Size: {{1.guests}}
📧 Email: {{1.email}}
📞 Phone: {{1.phone}}
Special Requests: {{1.requests}}
We look forward to serving you!
Best regards,
[Your Restaurant Name]
[Your Address]
[Your Phone]

### 6. Deploy HTML Form (15 minutes)

1. Download `reservation-form.html`
2. Open in text editor
3. Find line: `action="YOUR_MAKE_WEBHOOK_URL_HERE"`
4. Replace with your actual webhook URL from Step 4A
5. Customize styling/branding (optional)
6. Upload to your website or hosting

**Embedding Options:**

**Direct Embed:**
Copy entire HTML content into your webpage

**iFrame:**
```html
<iframe src="https://yoursite.com/reservation-form.html" 
        width="100%" height="800px" frameborder="0">
</iframe>
```

### 7. Test Everything (10 minutes)

1. Fill out test reservation on your form
2. Check Make.com execution log
3. Verify Google Sheet created/updated
4. Check email received
5. Test with different dates
6. Test error scenarios

### 8. Activate Scenario (1 minute)

1. In Make.com, toggle scenario to **ON**
2. Ensure scheduling is "Immediately as data arrives"
3. Monitor first few real reservations

## Troubleshooting

### Webhook not receiving data
- Check URL is correctly copied
- Verify CORS settings
- Test with Postman first

### Email not sending
- Verify Gmail connection
- Check email format
- Review Make.com logs

### Sheet not created
- Verify Spreadsheet ID
- Check Google permissions
- Test connection manually

## Next Steps

- Set up email alerts for failures
- Create backup/export workflow
- Add capacity management
- Implement SMS notifications

## Support

Open an issue on GitHub if you encounter problems.
