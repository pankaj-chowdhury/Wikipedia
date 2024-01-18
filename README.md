# Wikipedia API Request with Python

This repository contains a Python script that makes use of the `requests` library to fetch information from the Wikipedia API. The script is configured to retrieve content from the "2023_Cricket_World_Cup" Wikipedia page.

```python
import requests
endpoint = "https://en.wikipedia.org/w/api.php"
params = {
    "action": "query",
    "format": "json",
    "prop": "extracts",
    "exintro": True,
    "explaintext": True,
    "titles": "2023_Cricket_World_Cup"
}
response = requests.get(endpoint, params=params)
data = response.json()
page_data = data["query"]["pages"]
page_id = list(page_data.keys())[0]
page_info = page_data[page_id]
page_title = page_info["title"]
page_extract = page_info["extract"]

print(f"Title: {page_title}")
print(f"Extract:\n{page_extract}")
```
# Wikipedia Categories API Request with Python

This repository contains a Python script that utilizes the `requests` library to fetch category information from the Wikipedia API for the "2023_Cricket_World_Cup" page.

```python
import requests
endpoint = "https://en.wikipedia.org/w/api.php"
params = {
    "action": "query",
    "format": "json",
    "prop": "categories",
    "titles": "2023_Cricket_World_Cup"
}
response = requests.get(endpoint, params=params)
data = response.json()
page_data = data["query"]["pages"]
page_id = list(page_data.keys())[0]
page_info = page_data[page_id]
categories = page_info.get("categories", [])

category_names = [category["title"] for category in categories]

print(f"Categories: {', '.join(category_names)}")
```
# Wikipedia Pageviews API Request with Python

This repository contains a Python script that utilizes the `requests` library to fetch pageview data from the Wikipedia API for the "Lakshadweep" page.

```python
import requests
endpoint = "https://en.wikipedia.org/w/api.php"
params = {
    "action": "query",
    "format": "json",
    "prop": "pageviews",
    "titles": "Lakshadweep",
    "pvipdays": 10  # Number of days for which you want pageview data
}
response = requests.get(endpoint, params=params)
data = response.json()
page_data = data["query"]["pages"]
page_id = list(page_data.keys())[0]
page_info = page_data[page_id]
page_title = page_info["title"]
page_views = page_info["pageviews"]

print(f"Title: {page_title}")
print("Pageviews:")

for date, views in page_views.items():
    print(f"{date}: {views}")
```
# Wikipedia Search API Request with Python

This repository contains a Python script that utilizes the `requests` library to perform a search on Wikipedia for pages related to "domestic violence."

```python
import requests
endpoint = "https://en.wikipedia.org/w/api.php"
search_term = "domestic violence"

params = {
    "action": "query",
    "format": "json",
    "list": "search",
    "srsearch": search_term
}
response = requests.get(endpoint, params=params)
data = response.json()
search_results = data["query"]["search"]

print("Wikipedia pages related to 'domestic violence':")
for result in search_results:
    page_title = result["title"]
    print(page_title)
```

# Wikipedia Search API Request with Python (Total Hits)

This repository contains a Python script that utilizes the `requests` library to perform a search on Wikipedia for pages related to "domestic violence" and retrieves the total number of hits.

```python
import requests
endpoint = "https://en.wikipedia.org/w/api.php"
search_term = "domestic violence"

params = {
    "action": "query",
    "format": "json",
    "list": "search",
    "srsearch": search_term
}
response = requests.get(endpoint, params=params)
data = response.json()
search_results = data["query"]["search"]

print("Wikipedia pages related to 'domestic violence':")
for result in search_results:
    page_title = result["title"]
    print(page_title)
```
