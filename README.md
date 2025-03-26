## *Lagos Hotels Data Scraper*  

### **Project Overview**  
This simple project scrapes hotel information from <a href="https://hotels.ng/hotels-in-lagos" target="_blank">Hotels.ng</a> for all listed hotels located in Lagos, Nigeria.

### **Project Description**
This project utilizes Python's `requests` library and `Beautiful Soup` to extract hotel data from <a href="https://hotels.ng/hotels-in-lagos" target="_blank">Hotels.ng</a> website, specifically focusing on hotels located in Lagos, Nigeria. The scraped data includes hotel names, addresses, prices, ratings, and other relevant details.   

### **Problem Statement**  
The hospitality industry in Lagos, Nigeria, is rapidly growing, with a wide range of hotels catering to diverse needs. However, there is a lack of readily available, consolidated data on hotel pricing, locations, ratings, facilities, etc. This makes it difficult for potential customers to make informed decisions and for businesses to conduct effective market research. This project aims to address this gap by scraping and compiling hotel data from <a href="https://hotels.ng/hotels-in-lagos" target="_blank">Hotels.ng</a>, providing a valuable resource for both consumers and businesses. 

---
### Technologies Used
* Python: Core programming language.
* BeautifulSoup: For parsing HTML and extracting data.
* Requests: For making HTTP requests.
* Pandas: For exporting to CSV.

### Data Fields
The scraped data includes the following fields:
* Hotel Name
* Address
* Price
* Rating
* Review
* Facilities

### Data Output
The data is saved into a `.csv` file, that can be used for analysis.

### How It Works

* Sends requests to <a href="https://hotels.ng/hotels-in-lagos" target="_blank">Hotels.ng</a> and retrieves HTML content.
* Parses hotel details using BeautifulSoup.
* Iterates through all pages to capture complete hotel listings.
* Saves the collected data into a CSV file for easy access.

### Limitations
The scraper is dependent on the structure of the <a href="https://hotels.ng/hotels-in-lagos" target="_blank">Hotels.ng</a> website. Changes to the website may require updates to the scraper.

---

### Author
*UGWUANYI, ANTHONY C.*

**LinkedIn:** <a href="https://www.linkedin.com/in/chibi-ugwuanyi-663835252/" target="_blank">chibi-ugwuanyi-663835252/</a>

**E-mail:** <a href="https://mail.google.com" target="_blank">chibiugwuanyi@gmail.com</a>
