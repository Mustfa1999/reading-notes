# Reading: Class 17

> [Back to the main](./README.md)

---

## Web Scraping

Web scraping is a technique to automatically access and extract large amounts of information from a website, which can save a huge amount of time and effort. In this article, we will go through an easy example of how to automate downloading hundreds of files from the New York MTA. This is a great exercise for web scraping beginners who are looking to understand how to web scrape. Web scraping can be slightly intimidating, so this tutorial will break down the process of how to go about the process.

--- 

# Important Web Scrapping modules in python

## urllib.request & bs4 (Web Scraping)

```
import urllib.request 
from bs4 import BeautifulSoup as soup
import re
```

	page = urllib.request.urlopen("https://mikroelectron.com/") : save the URL
	soup = bs(page) : enter the URL
	names  = soup.body.findAll("h4") : find all the “h4” tags and save their elements in (names)
	names2 = re.findall("data-original-title=.\w+", str(names)) : extract the part from each one of (names) that has the string “data-original-title=”, and the “.\w+" part is to get the first word of each one

	container = page_soup.findAll("div", {"class": "list_item"})
	container[1].div.div.a['title']
	
## selenium

    from selenium import webdriver

    driv = webdriver.Chrome()

create a web browser object

    driv.get("https://www.youtube.com/watch?v=eDrFWRi13DY")
	
open that url on it

## requests 

	import requests
    import json

	API_URL = “https://api.themoviedb.org/3/movie/550?api_key=1234” 
    
we have to provide a valid authorized API URL with a valid API-key (not 1234)

	response = get(API_URL) 

using a GET request and saving the respond

	response = get(API_URL, params={"lat": 40.71, "lon": -74}) 
    
we can specify some parameters with the response like the longitude and the latitude 

	txt = response.text 
    
returns the contents of the response (JSON) as a string 

	jsonObj = response.json() 
    
returns the contents of the response (JSON) as a dictionary 

	statusCode = response.status_code  
    
returns the status code of the response (200 ~ 500)

    headers = response.headers 
    
returns the headers of the response

	print( json.dumps( jsonObj, sort_keys=True, indent=4) )
    
creates a formatted string of the Python JSON object

status codes meanings: https://restfulapi.net/http-status-codes/ 


## JSON

	from json import *
	pyDict = {"name":"John", "age":30, "city":"New York"}

	load( ‘{"name":"John", "age":30, "city":"New York"}’ ) 
    
converts from JSON string to Python dictionary 

	dumps( pyDict ) 
    
converts from Python dictionary to JSON string 

	print (dumps( pyDict, indent=4 ) ) 
    
we can specify the number of initial left indents (spaces) we want to print to give the output a pretty look

	print (dumps(pyDict, indent=4, separators=(". ", " = ") ) ) 
    
that will replace all the commas ( , ) to dots ( . ), and all the colons ( : ) to equal signs ( = )
    
    print (dumps(pyDict, indent=4, sort_keys=True ) ) 
    
that will sort the elements alphabetically 







