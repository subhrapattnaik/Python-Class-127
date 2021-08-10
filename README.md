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


Next, we are creating a for loop to iterate over all the ul_tags inside soup.find_all(“ul”, attrs={“class”:“exoplanet”}), meaning that it will final
all the ul_tags with class exoplanet.

----------------
Next, let’s again check the HTML with google inspect to see what’s inside the ul tag.

Here, we can see that it consists of li tags inside which we can get data. Again, we will need to iterate over all the li tags. For this, we will find all the
li tags.

now all we have to do is to iterate over these li tags and fetch the data, create a temporary list and then finally append that list into the
planet_data list that we created earlier
--------
Let’s inspect the li tags a bit deeper.
Here, we can see that the li tags have the name of the planet inside an anchor tag, and other details directly as HTML. For this, we need to make
sure that we treat the first li tag differently and others differently.


Let’s break it down line by line. We are first creating a temp_list to store all the data of this row.
Then, we are iterating over the li_tags we fetched earlier but this time, in a different way


Enumerate will give us both the index and the element on that index, instead of just the index that a traditional loop gives.
Using this index, if the index is 0 (first element), we are first finding the anchor tag inside the li_tag, and then
copying the inner HTML of it.Else, we want to directly copy the inner HTML of the li_tag.To facilitate this, in case a column is
empty and we get an error, we are going to use the try except block.Lastly, we will append this temp_listinto the planet_data.


Now, one final thing that we need to still figure out is, how to change the page by clicking on the next button.
Let’s check on the browser first -
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
