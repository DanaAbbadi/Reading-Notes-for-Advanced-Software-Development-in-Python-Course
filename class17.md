# Web Scrape

![img](https://res.cloudinary.com/practicaldev/image/fetch/s--KLJcR1tz--/c_imagga_scale,f_auto,fl_progressive,h_900,q_auto,w_1600/https://thepracticaldev.s3.amazonaws.com/i/mplqezmxfupbu7x7d90k.jpg)

Web scraping refers to the extraction of data from a website. This information is collected and then exported into a format that is more useful for the user. Be it a spreadsheet or an API.

Although web scraping can be done manually, in most cases, automated tools are preferred when scraping web data as they can be less costly and work at a faster rate.

But in most cases, web scraping is not a simple task. Websites come in many shapes and forms, as a result, web scrapers vary in functionality and features.

### How do Web Scrapers Work?

First, the web scraper will be given one or more URLs to load before scraping. The scraper then loads the entire HTML code for the page in question. More advanced scrapers will render the entire website, including CSS and Javascript elements.

Then the scraper will either extract all the data on the page or specific data selected by the user before the project is run.

Ideally, the user will go through the process of selecting the specific data they want from the page. For example, you might want to scrape an Amazon product page for prices and models but are not necessarily interested in product reviews.

Lastly, the web scraper will output all the data that has been collected into a format that is more useful to the user.

Most web scrapers will output data to a CSV or Excel spreadsheet, while more advanced scrapers will support other formats such as JSON which can be used for an API.

![img](https://www.parsehub.com/blog/content/images/2019/08/web-to-google-sheet-1.jpg)



## Python Code

Start by importing the following libraries.

        import requests
        import urllib.request
        import time
        from bs4 import BeautifulSoup

Next, we set the url to the website and access the site with our requests library.

    url = 'http://web.mta.info/developers/turnstile.html'
    response = requests.get(url)

If the access was successful, you should see the following output:

![img](https://miro.medium.com/max/518/1*fyqRGzG8IbhhjxF2Q5MU_Q.png)

Next we parse the html with BeautifulSoup so that we can work with a nicer, nested BeautifulSoup data structure. If you are interested in learning more about this library, check out the BeatifulSoup documentation.

    soup = BeautifulSoup(response.text, “html.parser”)

We use the method .findAll to locate all of our < a> tags.

    soup.findAll('a')

This code gives us every line of code that has an < a> tag. 

The information that we are interested in starts on line 38 as seen below. That is, the very first text file is located in line 38, so we want to grab the rest of the text files located below.

![img](https://miro.medium.com/max/728/1*G6YulYb5rczkVvmn7nbQ6g.png)

subset of all < a > tags

Next, let’s extract the actual link that we want. Let’s test out the first link.

    one_a_tag = soup.findAll(‘a’)[38]
    link = one_a_tag[‘href’]

This code saves the first text file, ‘data/nyct/turnstile/turnstile_180922.txt’ to our variable link. The full url to download the data is actually ‘http://web.mta.info/developers/data/nyct/turnstile/turnstile_180922.txt’. We can use our urllib.request library to download this file path to our computer. 

We provide request.urlretrieve with two parameters: file url and the filename. 

    download_url = 'http://web.mta.info/developers/'+ link
    urllib.request.urlretrieve(download_url,'./'+link[link.find('/turnstile_')+1:])

Last but not least, we should include this line of code so that we can pause our code for a second so that we are not spamming the website with requests. This helps us avoid getting flagged as a spammer.

    time.sleep(1)

























