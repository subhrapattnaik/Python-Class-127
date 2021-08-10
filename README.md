# Python-Class-127
Web Scraping

● Learn about web scraping
● Understand how tools like google inspect, selenium, etc. can
be used for our advantage
-----------------------------------------

 
Therefore in today’s class, we will learn about Web-Scraping, where we will write a program that can fetch all the data from NASA's website for us.

-------------------------------------------------------------------------------

Teacher opens the link from Teacher activity 1

https://exoplanets.nasa.gov/exoplanet -catalog/


we will scrape this website’s data. In this website, there is data present for about 4,277 exo-planets in 428 pages. 
---------------------------------------------------------
Let’s start by creating a virtual environment in a new directory -
python3.8 -m venv venv

venv\Scripts\activate.bat

---------------------
for mac:
source venv/bin/activate
-------------------------
let’s pip install a few modules -
pip install bs4
pip install selenium

bs4 (​BeautifulSoup​) ​is a python module, which is famously used for parsing text as HTML and then performing actions in it, such as finding specific HTML tags with a particular class/id, or listing out all the li tags inside the ul tags.



Selenium, on the other hand, is used to interact with the webpage. It is famously used for automation testing, such as testing the functionality of a website (Login/Logout/etc.) but can be also used to interact with the page such as clicking a button, etc.


Since we have to scrape data from 428 pages, clicking on the button to go to the next page would come in handy.
Selenium opens up the webpage in a browser.

-----------------------------------------------------------

Create a new file in your directory where you created the virtual environment, and name it as scraper.py.

Code:
import the libraries
make our code sleep for some time, so that the web-page could load properly before we start scraping. We are importing csv so that we can export the data that we scrape into CSV.

open the link we want to scrape with Chrome browser using Selenium -

 START_URL​ ​= "https://exoplanets.nasa.gov/exoplane t-catalog/"
 
 
 Inside the headers, I have the name of the columns I can see on the table mentioned in the web-page we are scraping, and the planet_data would be to save all the details of the planet. We will create a csv from these lists.
 
 
 let’s just try to scrape the first page only.
Before we do that, let’s inspect the page. We can see that all the rows in the table are ​ul​ tags with ​class​ as exoplanet​


Therefore, we need to find all the ul tags with class exoplanet in order to scrape the data.

Earlier, the chrome window we opened with Selenium, we named it as browser. Now, we are creating a BeautifulSoup object where we are
passing the browser’s page source and asking our bs4 to use html.parser in it, which means it will read the page as an HTML.



---------------------------------
chromedriver:

It’s a driver that will help us open chrome browser with Selenium. For that, we will have to download it from the following link -

https://chromedriver.chromium.org/downloads

Once downloaded, your /path/to/chromedriver​ should be the path where it is downloaded. 
For ease, you can have it in the same folder as your code.


If you are a mac user, there is one additional step involved after the chromedriver is installed. Run the following command in your terminal -

 xattr -d com.apple.quarantine /path/to/chromedriver

MacOS in general is heavily protected from spam or risky softwares, and it does not trust the drivers downloaded from the web. By doing the step above, we are letting Apple know to not quarantine the driver we just downloaded and trust it.
-----------------------------------------------------------------------
