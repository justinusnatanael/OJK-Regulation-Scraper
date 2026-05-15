# OJK Regulation Web Scraper and Task Scheduler

## Overview
This project is an automated web scraping solution designed to extract financial regulation data from the official OJK (Otoritas Jasa Keuangan) website. The primary purpose is to monitor and collect the latest regulatory updates in the Indonesian financial sector. The tool identifies regulation titles and their corresponding document links, providing a structured dataset for compliance monitoring or legal research. Additionally, it features a scheduling mechanism to ensure the data stays current without manual intervention.

## Goals
The primary goal of this project is to demonstrate the practical application of web scraping and process automation in a corporate or regulatory context. Key objectives include:
- **Automated Data Retrieval:** Implementing a robust scraping algorithm to navigate multi-page web structures.
- **Data Structuring:** Transforming unstructured HTML content from the OJK portal into a clean, structured pandas DataFrame.
- **Task Automation:** Integrating a scheduling system that allows the scraper to run periodically at specific intervals.
- **Resource Monitoring:** Capturing and storing links to original regulatory documents (PDFs) for direct access.

## Data Source
The data is sourced directly from the **OJK (Otoritas Jasa Keuangan) Regulation Portal**. The scraper extracts the following information:
- **Regulation Title:** The full descriptive name of the regulation.
- **Document Link:** The direct URL to the official regulation file (typically a PDF).
- **Metadata:** Page numbers and sequence of regulatory postings.

## Methodology
The project follows a modular approach to web scraping and automation:

### 1. Web Scraping Engine
A custom scraping function `scrape_ojk_regulations_with_links()` was developed using Python's most popular libraries:
- **Requests:** Used to handle HTTP requests and retrieve the raw HTML content from the target URL.
- **BeautifulSoup4:** Employed for parsing the HTML document and navigating the DOM to locate specific data elements (titles and links).
- **Multi-page Navigation:** The script uses a looping mechanism to iterate through sequential pages of the OJK portal, ensuring comprehensive data collection.

### 2. Data Processing
- **Parsing:** Specifically targeting `div` and `a` tags that house the regulatory information.
- **Validation:** Implementing checks to ensure that only valid responses (HTTP 200) are processed, preventing errors due to server downtime or incorrect URLs.
- **Storage:** Utilizing **Pandas** to aggregate the results into a tabular format, which can be easily exported for further analysis.

### 3. Scheduling & Automation
To move beyond a one-time script, the project implements:
- **Schedule Library:** Used to define "jobs" that the script should execute automatically.
- **Infinite Loop Architecture:** A controlled `while` loop that listens for pending tasks and executes them at the pre-defined schedule (e.g., every minute or daily).
- **Time Management:** Integrating the `time` library to manage system sleep intervals, reducing CPU overhead during idle periods.

---

## Results
The implementation successfully creates an automated pipeline that can:
- Scrape multiple pages of the OJK website in seconds.
- Generate a structured list of regulatory titles and direct download links.
- Run continuously as a background process, ensuring that new regulations are captured as soon as they are published.

## Future Work
To enhance the system further, the following features are planned:
- **Notification System:** Integrating email or Telegram bots to alert users immediately when a new "CIMB Niaga" relevant or general OJK regulation is detected.
- **Database Integration:** Storing historical data in a SQL database (e.g., PostgreSQL) to track changes in regulations over time.
- **Headless Browser Integration:** Using Selenium or Playwright to handle pages that may require JavaScript rendering in the future.

## Conclusion
This project demonstrates how Python can be used to bridge the gap between static web information and dynamic automated monitoring. By combining web scraping with task scheduling, it provides a powerful tool for financial institutions or legal firms to stay compliant with the ever-changing regulatory landscape of the OJK.
