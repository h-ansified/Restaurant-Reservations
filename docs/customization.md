markdown# Customization Guide

## Form Customization

### Change Colors

#### Primary Color Scheme
In `reservation-form.html`, find:
```css
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
```

Popular alternatives:
```css
/* Ocean Blue */
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);

/* Sunset Orange */
background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);

/* Forest Green */
background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);

/* Royal Purple */
background: linear-gradient(135deg, #a8edea 0%, #fed6e3 100%);
```

#### Form Border & Shadow
```css
border-radius: 16px; /* More rounded: 24px, Less: 8px */
box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08); /* Stronger: 0.15 */
```

### Add New Form Fields

#### Example: Add "Occasion" field

**1. In HTML (after guests field):**
```html

    Special Occasion
    
        Select...
        Birthday
        Anniversary
        Business Dinner
        Other
    

```

**2. In Make.com Blueprint:**
- Edit Modules 5 & 7 (Add Row)
- Add new column mapping: `"7": "{{1.occasion}}"`
- Update column range if needed

**3. In Email Template:**
🎉 Occasion: {{1.occasion}}

### Change Restaurant Branding

Replace header section:
```html
<div class="form-header">
    <h2>🍽️ [Your Restaurant Name]</h2>
    <p>[Your Tagline]</p>
</div>
```

Add logo:
```html
<div class="form-header">
    <img src="your-logo.png" alt="Logo" style="width: 120px; margin-bottom: 15px;">
    <h2>[Your Restaurant Name]</h2>
    <p>[Your Tagline]</p>
</div>
```

### Time Slot Restrictions

Limit available times (in JavaScript section):
```javascript
// After date input setup, add:
const timeInput = document.getElementById('res_time');
timeInput.setAttribute('min', '11:00'); // Earliest time
timeInput.setAttribute('max', '21:00'); // Latest time
timeInput.setAttribute('step', '900'); // 15-minute intervals
```

### Guest Number Limits

Adjust in HTML:
```html
<input type="number" id="res_guests" name="guests" 
       min="1" max="20" placeholder="2" required>
```

Change `max="20"` to your capacity limit.

## Make.com Customization

### Add SMS Notifications

**Module to Add:** After email modules

1. Add new module: SMS by Twilio
2. Connect Twilio account
3. Map fields:
To: {{1.phone}}
Message: "Reservation confirmed for {{1.name}} on {{1.date}} at {{1.time}}"

### Add Slack Notifications

For internal team notifications:

1. Add Slack module
2. Connect workspace
3. Configure:
Channel: #reservations
Message: "New reservation: {{1.name}} - {{1.guests}} guests on {{1.date}} at {{1.time}}"

### Add Calendar Integration

Add Google Calendar module:
Event Name: "Reservation - {{1.name}}"
Start: {{1.date}} {{1.time}}
Duration: 2 hours
Description:
Guests: {{1.guests}}
Phone: {{1.phone}}
Email: {{1.email}}
Requests: {{1.requests}}

## Email Template Customization

### HTML Email (Advanced)

Change body type from "collection" to "rawHtml":
```html
<!DOCTYPE html>
<html>
<head>
    <style>
        body { font-family: Arial, sans-serif; }
        .container { max-width: 600px; margin: 0 auto; padding: 20px; }
        .header { background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; padding: 20px; text-align: center; }
        .content { background: #f9f9f9; padding: 20px; }
        .detail { margin: 10px 0; }
        .footer { text-align: center; color: #666; padding: 20px; }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>Reservation Confirmed!</h1>
        </div>
        <div class="content">
            <p>Dear {{1.name}},</p>
            <p>Your reservation has been confirmed:</p>
            <div class="detail">📅 <strong>Date:</strong> {{1.date}}</div>
            <div class="detail">🕐 <strong>Time:</strong> {{1.time}}</div>
            <div class="detail">👥 <strong>Guests:</strong> {{1.guests}}</div>
        </div>
        <div class="footer">
            <p>We look forward to serving you!</p>
            <p>[Your Restaurant] | [Address] | [Phone]</p>
        </div>
    </div>
</body>
</html>
```

### Add Attachments

In email module, add attachment:
- Menu PDF
- Parking instructions
- Directions map

## Google Sheets Customization

### Add Formatting

Create Google Apps Script:
```javascript
function formatNewSheet() {
  var sheet = SpreadsheetApp.getActiveSheet();
  
  // Header row formatting
  var headerRange = sheet.getRange("A1:G1");
  headerRange.setBackground("#667eea");
  headerRange.setFontColor("#ffffff");
  headerRange.setFontWeight("bold");
  
  // Set column widths
  sheet.setColumnWidth(1, 150); // Name
  sheet.setColumnWidth(2, 200); // Email
  sheet.setColumnWidth(3, 130); // Phone
  // etc...
}
```

### Add Conditional Formatting

Highlight VIP guests, large parties, special occasions automatically.

## Advanced Features

### Capacity Management

Track available slots per time:
1. Create "Capacity" sheet in Google Sheets
2. Add lookup module in Make.com
3. Check availability before confirming
4. Send "Fully Booked" email if unavailable

### Multi-Location Support

Add location selector in form:
```html
<select id="res_location" name="location">
    <option value="downtown">Downtown Location</option>
    <option value="beachfront">Beachfront Location</option>
</select>
```

Route to different spreadsheets based on location.

### Cancellation Link

In email, add:
```html
<a href="https://your-cancellation-form.com?id={{moduleID}}">Cancel Reservation</a>
```

Create separate cancellation scenario.

## Styling Examples

### Minimalist Style
```css
/* Clean, simple look */
border-radius: 4px;
box-shadow: 0 2px 8px rgba(0,0,0,0.05);
background: linear-gradient(to bottom, #ffffff 0%, #f8f9fa 100%);
```

### Bold & Modern
```css
/* High contrast, bold */
border-radius: 20px;
box-shadow: 0 8px 30px rgba(0,0,0,0.12);
background: linear-gradient(135deg, #6366f1 0%, #8b5cf6 100%);
```

### Classic & Elegant
```css
/* Traditional restaurant feel */
border-radius: 0;
box-shadow: 0 2px 4px rgba(0,0,0,0.1);
border: 3px solid #2c3e50;
background: #ffffff;
