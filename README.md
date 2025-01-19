#hotels.ng
#Web scraping - hotels
#This code scrapes hotels.ng for hotels in Lagos, Nigeria

import time
import requests
from bs4 import BeautifulSoup
import pandas as pd

#Initialize variables
base_url = 'https://hotels.ng/hotels-in-lagos'
next_page = 1
hotel_details = []

while True:
    try:
        # Fetch the page
        url = f'{base_url}/{next_page}'
        response = requests.get(url)
        if response.status_code != 200:
            print(f"Failed to fetch page {next_page}. Status code: {response.status_code}")
            break
        
        soup = BeautifulSoup(response.text, 'lxml')

        # Find all hotels on the current page
        hotels = soup.find_all('div', class_='listing-hotels')
        if not hotels:
            print("No more hotels found. Ending scrape.")
            break

        for hotel in hotels:
            # Extract hotel details
            hotel_name = hotel.find('h2', itemprop='name')
            hotel_name = hotel_name.text.strip() if hotel_name else 'Missing'

            hotel_address = hotel.find('p', itemprop='address')
            if hotel_address:
                address_parts = hotel_address.text.split()
                hotel_area = " ".join(address_parts[:2]).replace(',', '') if len(address_parts) > 1 else 'Missing'
                hotel_street = " ".join(address_parts[2:]).strip('- ') if len(address_parts) > 2 else 'Missing'
            else:
                hotel_area = 'Missing'
                hotel_street = 'Missing'

            hotel_price = hotel.find('p', class_='listing-hotels-prices-discount')
            hotel_price = hotel_price.text.strip().split()[0] if hotel_price else 'Missing'

            hotel_rating = hotel.find('p', class_='listing-hotels-rating')
            hotel_rating = hotel_rating.text.strip().split()[0] if hotel_rating else 'Missing'

            hotel_review = hotel.find('p', class_='listing-hotels-rating-number')
            hotel_review = " ".join(hotel_review.text.strip().split()[1:]) if hotel_review else 'Missing'

            hotel_facilities = hotel.find('div', class_='listing-hotels-facilities d-none d-md-flex')
            hotel_facilities = ", ".join(hotel_facilities.text.split()) if hotel_facilities else 'Missing'

            # Append to list
            hotel_details.append({
                'Name': hotel_name,
                'Area': hotel_area,
                'Street': hotel_street,
                'Price': hotel_price,
                'Rating': hotel_rating,
                'Reviews': hotel_review,
                'Facilities': hotel_facilities
            })

        print(f"Scraped page {next_page}.")
        next_page += 1
        time.sleep(2)  # Avoid overloading the server

    except Exception as e:
        print(f"An error occurred: {e}")
        break

#Save data to CSV
df = pd.DataFrame(hotel_details)
df.to_csv('lagos_hotels.csv', index=False)
print("Scraping completed. Data saved to 'lagos_hotels.csv'.")
