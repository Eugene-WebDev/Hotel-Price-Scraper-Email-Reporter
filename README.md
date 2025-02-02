# Hotel-Price-Scraper-Email-Reporter

**Features**

Scrapes hotel prices for 45 days ahead from Booking.com
Uses Selenium WebDriver with random User-Agents to avoid detection
Stores extracted data in CSV format
Sends email reports with price details as attachments
Implements retry mechanisms for both scraping and email sending
Automatically runs daily at 00:35 using schedule

**Technologies Used**

Python (Selenium, SMTP, Schedule)
Selenium WebDriver (for scraping)
SMTP2GO (for sending emails)

**Usage**

To run the scraper manually:

_python scraper.py_  

The script will:

Scrape hotel prices
Save data in a CSV file
Send an email report

**Automation**

The script runs daily at 00:35 using schedule. To ensure continuous execution:

Run in the background (Linux/Mac):

_nohup python scraper.py &_ 

Or set up a cron job:

_crontab -e_

Add the following line:

_35 0 * * * /usr/bin/python3 /path/to/scraper.py_  
