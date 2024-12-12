# JobTracker

An AI tool to track job applications by analysing your email using OpenAI's GPT, and saving the relevent job data in Google Sheets so you don's have to.

## Features

- 📧 Manual trigger (run notebook) to check your Yahoo email inbox for job application-related emails
- 🔄 Processes MAX_EMAILS emails. MAX_BATCH_SIZE reconnects with Yahoo Mail Server handle larger volumes.
- 🤖 Uses OpenAI's GPT to intelligently analyze email content
- 🔍 Detects application status (Applied, Rejected, Interview Request, Viewed)
- 📊 Saves job application data in Google Sheets
- 🎯 Avoids duplicate entries

## Prerequisites

- Python 3.x
- A Yahoo email account
- Google Cloud Platform account
- OpenAI API account

## Required API Keys & Credentials

1. **Google Service Account JSON Key**
   - Follow the detailed setup guide in the notebook for Google Cloud Platform setup
   - Enable Google Sheets API
   - Create a service account and download the JSON key

2. **OpenAI API Key**
   - Sign up for OpenAI API access
   - Generate an API key from your OpenAI dashboard

3. **Yahoo App Password**
   - Generate an app-specific password for this application

## Installation

1. Clone the repository:

git clone https://github.com/tommyyau/JobTracker.git

2. Install required packages:

bash
pip install openai google-api-python-client google-auth-httplib2 google-auth-oauthlib


## Configuration

Update the `Config` class in the script with your credentials and the number of email you want processed:

1. SERVICE_ACCOUNT_FILE = 'path/to/your/service-account-key.json'
2. SPREADSHEET_ID = 'your-google-sheet-id'
3. OPENAI_API_KEY = "your-openai-api-key"
4. EMAIL_SERVER = 'imap.mail.yahoo.com'
5. EMAIL_USER = 'your-yahoo-email@yahoo.com'
6. EMAIL_PASSWORD = 'your-yahoo-app-password'
7. MAX_EMAILS = 50 # Number of recent emails to check
8. MAX_BATCH_SIZE = 200 # Batch size for processing


## Usage

Run the Jupyter notebook or execute the script:

jupyter notebook JobTracker-OpenAI-WithMaskCredentials.ipynb


The script will:
1. Connect to your Yahoo email
2. Scan recent emails for job application-related content
3. Analyze each relevant email using OpenAI's GPT
4. Extract job details (title, company, status)
5. Store the information in your Google Sheet

## Google Sheet Structure

The script creates entries with the following columns:
- Job Title
- Company Name
- Application Status
- Date Received
- Sender Email

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request and I try and figure what I need to do next :).

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Security Notes

- Never commit your API keys or credentials to version control
- Store sensitive information in environment variables or secure configuration files
- Regularly rotate your API keys and passwords
- Monitor your API usage to avoid unexpected charges

## Acknowledgments

- OpenAI for providing the GPT API
- Google Cloud Platform for Sheets API
- Yahoo for IMAP email access
