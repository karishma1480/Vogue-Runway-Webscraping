# Vogue Runway - Webscraping

## Project Overview
For this project, my objective was to scrape images from Vogue Runway's fashion show collections, with a particular focus on specific seasons and brands, such as Gucci's Resort 2025 runway collection. The goal was to automate the process of collecting, downloading, and resizing these fashion show images, which would later be used for further analysis and trend forecasting. This would enable a comprehensive understanding of emerging fashion trends across multiple collections and brands.

## Data Used
The data used in this project are fashion show images from the Vogue Runway website, particularly focusing on Gucci's Resort 2025 runway collection. The images come from HTML elements containing multiple image sets per collection, which need to be extracted and processed.

<img width="1919" height="986" alt="image" src="https://github.com/user-attachments/assets/90d62b1f-6342-4938-8d3d-660a3d1de582" />

## Data Preparation
**1. Selenium WebDriver:** Selenium WebDriver is a tool for automating web browsers. It allows you to programmatically control a browser, interact with elements like buttons, dropdowns, and forms, and extract data from dynamic web pages. In this project, Selenium is used to navigate the Vogue Runway website, log in, and interact with dynamically loaded content, such as clicking the "Next" button and selecting options from dropdowns. It is effective because it can simulate real user interactions and handle dynamic content that changes or loads based on user inputs, making it essential for scraping pages with JavaScript-driven elements.

**2. BeautifulSoup:** BeautifulSoup is a Python library used to parse HTML and XML documents. It creates a parse tree that allows for easy extraction of data from HTML structures using methods like find() and select(). After Selenium loads the web page, BeautifulSoup is used to efficiently parse the page’s HTML and extract the image URLs. It’s effective because it simplifies navigating through the HTML structure, identifying specific elements (like image tags), and extracting the desired information, making it ideal for web scraping tasks that don’t need user interaction.

**3. Requests:** Requests is a Python library for sending HTTP requests to web servers. It handles all the complexity of making a web request, allowing you to download content like images, files, or web pages. Once the image URLs are extracted, Requests is used to download the images by sending a simple HTTP GET request. It is effective because it provides a straightforward and reliable way to retrieve web content, and it handles various aspects of downloading such as response status and error handling, ensuring that the images are properly fetched.

**4. PIL (Python Imaging Library):** PIL, or its more modern version Pillow, is a library for image processing in Python. It allows for opening, manipulating, and saving image files. In this project, PIL/Pillow is used to resize the downloaded images to a consistent size (300x300). This is effective for ensuring uniformity in image size for further analysis, as it makes images more manageable in terms of storage and easier to process for machine learning or visualization tasks.

**5. OS:** The OS module in Python provides a way to interact with the operating system, allowing file and directory manipulation. OS is used to create directories where images are saved (os.makedirs) and to handle file paths when downloading images. It’s effective because it allows the script to dynamically create and manage folders, ensuring the images are stored in an organized manner without manual intervention.

**6. Time:** The Time module provides functions for manipulating time, such as delays using time.sleep(). Time is used to introduce delays in the script to allow the webpage to load fully before proceeding with actions like scraping or clicking buttons. It’s effective in ensuring the web scraper does not attempt to interact with elements before they are available, preventing errors and improving reliability in dynamic content.


## Summary of Code

I configured Chrome WebDriver and automated login to Vogue, then navigated to the Gucci Resort 2025 collection. Using BeautifulSoup, I parsed the page HTML to extract image URLs from specific elements. I implemented pagination handling to click through multiple image sets and added duplicate prevention to avoid re-scraping the same images. Downloaded images were automatically resized to 300x300 pixels and saved to a designated folder. The script included error handling and terminated after completing all downloads.

- I combined Selenium and BeautifulSoup because Vogue Runway uses JavaScript-driven dynamic elements like dropdowns and pagination buttons. Selenium handled user interactions while BeautifulSoup efficiently parsed HTML to extract image URLs.
- WebDriverWait and time delays ensured elements fully loaded before interaction, preventing errors with dynamic content and pagination.
- I avoided headless mode to simplify debugging and prevent element rendering issues, and skipped parallel requests to avoid triggering anti-scraping mechanisms.
- Images were resized to uniform dimensions using PIL/Pillow during download, and set-based URL tracking prevented duplicate downloads when encountering repeated image sets.

