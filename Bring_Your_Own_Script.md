# About

**Category:**  WEB

**Question:**  Bring Your Own Script

**Flag:**  RWSC{J4CKP0T}

# How to solve

I wrote a script to recursively search through a website that has a nested structure with dozens of subdirectories stemming from the root page, and further subdirectories within those, reaching a maximum depth of about 15 levels. This script is designed to save the HTML of all those endpoints. Essentially, all the HTML files contain either `'No directories found.'` or have `<li>` tags, so I surmised that the HTML files without these are where the flag is hidden, and included this in my conditions. Ultimately, I discovered an endpoint returning HTML with an image and found the flag.

# The html code that has flag

[The Link Here](https://byos.ctf.rawsec.com/root/%F0%9F%A4%A4%F0%9F%A4%95%F0%9F%98%83/%F0%9F%98%94%F0%9F%98%81%F0%9F%98%95%F0%9F%98%B5/%F0%9F%98%BA%F0%9F%98%AA%F0%9F%A5%B4%F0%9F%98%87/%F0%9F%A5%B0%F0%9F%A5%B6%F0%9F%A4%A3%F0%9F%98%82/%F0%9F%A4%A7%F0%9F%98%85/index.php)

```https://byos.ctf.rawsec.com/root/%F0%9F%A4%A4%F0%9F%A4%95%F0%9F%98%83/%F0%9F%98%94%F0%9F%98%81%F0%9F%98%95%F0%9F%98%B5/%F0%9F%98%BA%F0%9F%98%AA%F0%9F%A5%B4%F0%9F%98%87/%F0%9F%A5%B0%F0%9F%A5%B6%F0%9F%A4%A3%F0%9F%98%82/%F0%9F%A4%A7%F0%9F%98%85/index.php```

```html
<!DOCTYPE html>
<html lang="en">
 <head>
  <meta charset="utf-8"/>
  <meta content="width=device-width, initial-scale=1.0" name="viewport"/>
  <title>
   Image Display
  </title>
 </head>
 <body>
  <img alt="8hss4p.jpg" src="8hss4p.jpg" style="max-width: 100%;"/>
  <img alt="8hss31.jpg" src="8hss31.jpg" style="max-width: 100%;"/>
 </body>
</html>
```

![image](https://github.com/hiroyuki01233/RentasCTF-FreshHacker/assets/49856822/9444e32a-eec8-49f0-90cc-4b874ab1a469)


## Here is a script to scrape

```python
# Updated code with functionality to save all scraped HTML pages to a directory
import requests
from bs4 import BeautifulSoup
from urllib.parse import urljoin, quote, urlparse, urldefrag
import os


def save_html_to_file(soup, url, directory):
    """
    Save the BeautifulSoup object as an HTML file in the specified directory.
    The filename is derived from the URL.
    """
    # Parse the URL to create a valid filename
    parsed_url = urlparse(url)
    filename = (f"{parsed_url.netloc}{parsed_url.path}".replace('/', '_').replace('%', '_'))[:250] + ".html"
    filepath = os.path.join(directory, filename)

    # Write the HTML content to the file
    with open(filepath, 'w', encoding='utf-8') as file:
        file.write(soup.prettify())

    print(f"Saved HTML to {filepath}")


import urllib.parse

def scrape_and_find_rwsc(url):
    # スクレイピングする関数
    def scrape(url):
        response = requests.get(url)
        soup = BeautifulSoup(response.content, 'html.parser')

        save_html_to_file(soup, url, "./html_directory")

        return soup

    # 再帰的にリンクをたどる関数
    def follow_links(url):

        print(url)
        soup = scrape(url)
        if "No directories found." not in soup.prettify() and "<li>" not in soup.prettify():
            # RWSCが含まれる場合、HTMLを出力して終了
            print(soup.prettify())
            return True

        for li in soup.find_all('li'):
            a = li.find('a')
            if a and 'href' in a.attrs:
                # 新しいURLを作成してたどる
                next_url = urllib.parse.urljoin(url, a['href'])
                if follow_links(next_url):
                    return True
        return False

    follow_links(url)

# スタートURL
start_url = 'https://byos.ctf.rawsec.com/root/index.php' 
scrape_and_find_rwsc(start_url)
```


## Here is a directory under htmls that are scraped

![Screenshot 2024-03-06 225956](https://github.com/hiroyuki01233/RentasCTF-FreshHacker/assets/49856822/49fcb13e-f9f2-4736-9389-c54577368ad5)
