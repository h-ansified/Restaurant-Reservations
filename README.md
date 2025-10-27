# 🍽️ Restaurant Reservation System

A complete restaurant reservation system that combines a beautiful frontend form with an automated backend workflow using Make.com (formerly Integromat).

## 🌟 Overview

This system allows customers to make restaurant reservations through a responsive web form, which automatically processes the booking, stores it in Google Sheets, and sends confirmation emails - all automated through Make.com.

## 🏗️ System Architecture

```
Frontend (HTML Form) → Make.com Webhook → Google Sheets + Email Confirmation
```

## 📁 Project Structure

```
restaurant-reservation-system/
│
├── index.html                 # Main reservation form
├── make-scenario.json         # Make.com automation blueprint
└── README.md                  # This file
```

## ✨ Features

### Frontend Form
- 📱 **Fully responsive design** - works on all devices
- ⚡ **Real-time validation** - ensures data quality
- 🎨 **Modern UI/UX** - beautiful gradients and animations
- 📧 **Instant feedback** - success/error messages
- 🔒 **Secure submission** - no page reload required

### Backend Automation
- 📊 **Automatic Google Sheets logging** - stores all reservations
- ✉️ **Email confirmations** - sent automatically to customers
- 📅 **Dynamic sheet creation** - new sheets for each date
- 🔄 **Error handling** - robust failure management

## 🚀 Quick Start

### 1. Frontend Setup

1. **Download** the `index.html` file
2. **Replace the webhook URL** in the form action:
   ```html
   <form id="reservationForm" method="POST" action="YOUR_MAKE_WEBHOOK_URL_HERE">
   ```
3. **Upload** to your web server or use with any hosting service

### 2. Backend Setup (Make.com)

1. **Import the scenario:**
   - Go to your Make.com dashboard
   - Click "Create a new scenario"
   - Import the `make-scenario.json` blueprint
   - Update connections with your Google and Gmail accounts

2. **Configure connections:**
   - **Google Sheets**: Connect to your Google account
   - **Gmail**: Set up email sending capabilities
   - Update the Spreadsheet ID with your actual Google Sheets document

3. **Get your webhook URL:**
   - Copy the webhook URL from the first module
   - Paste it into your HTML form's `action` attribute

## 🛠️ Configuration

### Form Fields
The system captures these reservation details:
- 👤 **Name** (required)
- 📧 **Email** (required)
- 📞 **Phone** (required)
- 📅 **Date** (required)
- ⏰ **Time** (required)
- 👥 **Number of Guests** (required)
- 💬 **Special Requests** (optional)

### Google Sheets Structure
Reservations are organized by date in separate sheets with columns:
- A: Name
- B: Email
- C: Phone
- D: Date
- E: Time
- F: Guests
- G: Special Requests

## 📧 Email Templates

**Confirmation Email Includes:**
- Customer name
- Reservation date and time
- Number of guests
- Contact information
- Special requests (if any)

## 🔧 Customization

### Styling
Modify the CSS in `index.html` to match your restaurant's branding:
- Change colors in the `:root` variables
- Update gradients in button styles
- Modify fonts and spacing

### Form Fields
Add or remove fields by:
1. Updating the HTML form
2. Modifying the Make.com scenario mappers
3. Adjusting Google Sheets columns

### Automation Logic
Extend the Make.com scenario to:
- Send SMS confirmations
- Integrate with calendar systems
- Add restaurant staff notifications
- Implement booking reminders

## 🌐 Deployment

### Option 1: Simple Hosting
Upload `index.html` to any web hosting service:
- Netlify
- Vercel
- GitHub Pages
- Traditional web hosting

### Option 2: Embed in Website
Copy the form HTML and CSS into your existing restaurant website.

### Option 3: WordPress
Use as a custom HTML block in your WordPress site.

## 🔒 Security Considerations

- ✅ Form validation prevents invalid submissions
- ✅ No sensitive data exposed in frontend code
- ✅ Make.com handles backend security
- ✅ Google Sheets access controlled via OAuth

## 📊 Monitoring & Maintenance

### Check System Health
- Monitor Make.com scenario executions
- Review Google Sheets for new reservations
- Check email delivery rates

### Regular Updates
- Test form functionality monthly
- Update dependencies as needed
- Review and optimize automation flows

## 🐛 Troubleshooting

### Common Issues

1. **Form not submitting**
   - Check webhook URL is correct
   - Verify Make.com scenario is active
   - Check browser console for errors

2. **Emails not sending**
   - Verify Gmail connection in Make.com
   - Check spam folders
   - Review Make.com execution logs

3. **Sheets not updating**
   - Confirm Google Sheets connection
   - Check spreadsheet permissions
   - Verify sheet naming format

## 📈 Extensions & Enhancements

Potential future enhancements:
- 📅 **Calendar integration** - sync with restaurant calendar
- 💳 **Payment processing** - require deposits for reservations
- ⭐ **Review system** - post-dining experience feedback
- 📊 **Analytics dashboard** - reservation insights and reporting
- 🔔 **Reminder system** - SMS/email reminders before reservation

## 🤝 Contributing

Feel free to fork this project and submit pull requests for:
- Bug fixes
- New features
- Documentation improvements
- Translation updates

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

**Need help?** Check the [Make.com documentation](https://www.make.com/en/help) or create an issue in this repository.

**⭐ Star this repo if you found it helpful!**
