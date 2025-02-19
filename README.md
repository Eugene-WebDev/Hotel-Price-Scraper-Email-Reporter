# Mail2 Book Scrape

A Python script that automates the process of scraping hotel prices from Booking.com and sending the results via email as CSV attachments. The script uses Selenium for web scraping and Schedule for daily automation.

## Features

- **Automated Scraping:** Retrieves hotel prices for a range of check-in dates (up to 45 days ahead) from Booking.com.
- **CSV Reporting:** Saves scraped data into CSV files for each hotel.
- **Email Notifications:** Sends out the CSV reports as email attachments using SMTP2GO.
- **Daily Scheduler:** Automatically runs the scraping job every day at a specified time (default is 00:40).

## Prerequisites

- **Python 3.6+**
- **Google Chrome Browser** installed on your system.
- **ChromeDriver:** Managed automatically by [webdriver_manager](https://pypi.org/project/webdriver-manager/).

## Dependencies

The script requires several Python packages. You can install them using pip:

```bash
pip install -r requirements.txt
```

A sample `requirements.txt` file might include:

```txt
selenium
webdriver-manager
schedule
```

Additionally, the script uses built-in modules such as `smtplib`, `email`, `csv`, `os`, `random`, `datetime`, and `time`.

## Setup

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/your_username/mail2_book_scrape.git
   cd mail2_book_scrape
   ```

2. **Configure Email Settings:**

   In the `mail2_book_scrape.py` file, update the SMTP settings with your SMTP2GO (or alternative) credentials:

   ```python
   SMTP_SERVER = "mail.smtp2go.com"
   SMTP_PORT = 2525  # or your chosen port
   EMAIL_ADDRESS = "your_email"
   EMAIL_PASSWORD = "your_password"
   ```

3. **Configure Hotel Details:**

   Modify the `config.py` file to update the list of hotels and the location:

   ```python
   hotel_names = [
       "qubuswroclaw",
       "arthotelwroclaw",
       "hpparkplazawroclaw",
       "monopol-wroclaw",
       "puro-wroclaw",
       "korona-market-square-wroclaw",
       "grand-city-wroclaw",
       "ac-by-marriott-wroclaw"
   ]

   # Define location
   location = "Wroclaw"
   ```

4. **User-Agent Configuration:**

   The script includes a pool of user agents to reduce the risk of being blocked. Feel free to add or modify user agents in the `USER_AGENTS` list.

## Usage

To run the script, simply execute:

```bash
python mail2_book_scrape.py
```

The script will start a scheduler that runs the scraping job daily at 00:40. You can modify the scheduling time by editing the following line in the script:

```python
schedule.every().day.at("00:40").do(daily_job)
```

If you need to run the job manually for testing, call the `daily_job()` function directly.

## Troubleshooting

- **Email Issues:** If emails fail to send, check your SMTP credentials and ensure that your email service provider allows SMTP connections.
- **Scraping Errors:** The script uses retries for scraping failures. If a hotel’s price isn’t scraped successfully after multiple attempts, the price will be marked as "Not Available" in the CSV.
- **Driver Problems:** Make sure your Google Chrome version is up to date. The `webdriver_manager` package should automatically handle driver installation.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for improvements or bug fixes.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Disclaimer

This script is intended for educational and personal use only. Make sure to comply with Booking.com's terms of service and any applicable laws when scraping data.

```

This README.md should serve as a clear guide for users to set up and run project on GitHub.
