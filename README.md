# SAN AGUSTIN YEP ID - Flask Web Application

A Flask web application for generating and scanning QR codes with user registration and admin authentication.

## Features

- 👤 User registration system with email QR code delivery
- 🔐 Admin login system
- 📱 Generate QR codes from text, URLs, or any data
- 🔍 Scan QR codes from uploaded images
- 💾 Download generated QR codes
- 📧 Automatic email delivery of QR codes after registration
- 🎨 Modern and responsive UI

## Installation

1. Install Python dependencies:
```bash
pip install -r requirements.txt
```

2. **Configure Email Settings** (Required for registration):
   
   The application uses Flask-Mail to send QR codes via email. You need to configure your email settings.
   
   **Option 1: Environment Variables (Recommended)**
   
   Set these environment variables before running the app:
   ```bash
   # For Gmail (use App Password, not regular password)
   set MAIL_SERVER=smtp.gmail.com
   set MAIL_PORT=587
   set MAIL_USE_TLS=true
   set MAIL_USERNAME=your-email@gmail.com
   set MAIL_PASSWORD=your-app-password
   set MAIL_DEFAULT_SENDER=your-email@gmail.com
   ```
   
   **Option 2: Edit app.py directly**
   
   Update the email configuration in `app.py` (lines 15-20):
   ```python
   app.config['MAIL_USERNAME'] = 'your-email@gmail.com'
   app.config['MAIL_PASSWORD'] = 'your-app-password'
   ```
   
   **Gmail Setup:**
   - Enable 2-Step Verification
   - Generate an App Password: https://myaccount.google.com/apppasswords
   - Use the App Password (16 characters) as MAIL_PASSWORD
   
   See `config_example.py` for other email provider settings.

3. Run the application:
```bash
python app.py
```

4. Open your browser and navigate to:
```
http://localhost:5000
```

## Default Login Credentials

- **Username:** `admin`
- **Password:** `admin123`

**Important:** Change the default password in production!

## Usage

### User Registration
1. When you visit the site, you'll be redirected to the registration page
2. Fill out the registration form with:
   - Full Name (required)
   - Email Address (required)
   - Phone Number (optional)
3. Click "Register"
4. Your unique QR code will be automatically generated and sent to your email
5. Check your inbox (and spam folder) for the email containing your QR code

### Admin Login
1. Click "Admin Login" from the registration page or go to `/login`
2. Use the default credentials:
   - Username: `admin`
   - Password: `admin123`
3. Access the admin dashboard to generate and scan QR codes

### Generate QR Code (Admin)
1. Log in with admin credentials
2. Navigate to "Generate" from the dashboard
3. Enter any text, URL, or data
4. Click "Generate QR Code"
5. Download the QR code if needed

### Scan QR Code (Admin)
1. Navigate to "Scan" from the dashboard
2. Upload an image file containing a QR code
3. The decoded data will be displayed

## Project Structure

```
.
├── app.py                    # Main Flask application
├── requirements.txt          # Python dependencies
├── config_example.py          # Email configuration example
├── users_data.json           # User registration data (auto-generated)
├── templates/                # HTML templates
│   ├── base.html
│   ├── register.html         # User registration page
│   ├── registration_success.html
│   ├── login.html
│   ├── dashboard.html
│   ├── generate.html
│   └── scan.html
├── static/                   # Static files
│   ├── style.css
│   └── qr_codes/            # Generated QR codes (auto-generated)
└── README.md
```

## Technologies Used

- Flask - Web framework
- Flask-Mail - Email functionality
- qrcode - QR code generation
- OpenCV (cv2) - QR code scanning/decoding
- Pillow - Image processing
- Werkzeug - Password hashing
- NumPy - Image processing support

## Security Notes

- Change the `secret_key` in `app.py` for production
- Update admin credentials or implement a proper user database
- Use environment variables for sensitive configuration (email credentials)
- Never commit email passwords or API keys to version control
- Consider adding rate limiting and CSRF protection
- For production, use a proper database instead of JSON file storage
- Implement email verification for user registrations

## License

This project is open source and available for use.

