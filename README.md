# TripAdvisorScraper

This was my second Python project. I wanted to build on what I had learned from my first project and build something more impressive. I had the idea to do what I had done with Metacritic in TripAdvisor, but instead of simply scraping and formatting text, I wanted a screenshot of the review. 

This project gave me experience using geckodriver and selenium, as well as bolstering what I had learned in my previous undertaking. This project comes with a file called 'cities.txt'. This is a list of cities from around the world for use within the program. It is taken from an open-source Excel spreadsheet and is used for searches within Selenium. 


**Steps**

1. city_select:

    This simple method opens up our cities.txt and picks a random line from the file. It will then print the selected city and pass it       to the city_entry method 

2. city_entry:

    city_entry is the method which takes us to the hotel selection page. It initially searched directly from the Tripadvisor website,       however numerous issues with popups meant this failed more often than not. As a workaround, it searches from Google, appending the       city selected to 'tripadvisor' in the search (e.g. 'Tripadvisor London'). Then we select the first result from the Google search         that is not an advertisement. When the page is loaded for the location, our Selenium webdriver clicks the 'Hotels' link to get the       list of hotels, returns the url and passes it to the 'hotel_select' method.
    
3. hotel_select:

    This method does not use the webdriver and instead uses BeautifulSoup in order to get a list of hotels from the provided URL. It         makes a random choice from the list of hotel urls, and passes it to review_select.
    
4. review_select:

    Our review_select method uses BeautifulSoup again to pick a review from a list of reviews. If there are no reviews available, the       method will point back to city_select. If a review is available, it will randomly pick a review and pass it to 'format_review'.
    
5. format_review:

    This final method takes the given user review URL and launches it in our webdriver. It extends the review content if there is any       text hidden behind a 'MORE' button. The final action of our webdriver is to take a screenshot of the review element                     'reviewSelector'. Using the Image import we can open this screenshot and save it as a PNG locally. The screenshot is named using a       random int between 0 and 999999999 and appending .png to the end. The filename will then be printed and stored for you to look at. 
    
    
**Footnotes**

Again, as was the case in my first Python side project, a lot of thought hasn't gone into the formatting as far as SOLID principles go. Nor with the commenting. At this point I was still very much getting to grips with the language and it's core concepts. 
