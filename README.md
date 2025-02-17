# News Scraper: A Web Scraping Project Using Scrapy

![img](https://user-images.githubusercontent.com/17881612/91968083-5ee92080-ed29-11ea-82ec-d99ec85367a5.png)

This project is designed to scrape News articles from multiple north eastern websites like [North East Now](https://assam.nenow.in/) using Scrapy. The goal is to create a structured dataset of news articles across different categories such as Business, Culture, Education, Entertainment, Health, Literature, Sports, Technology, and Youth Voice.

## Features

- **Automated Web Scraping**: Uses Scrapy to extract article titles from multiple categories.
- **Pagination Handling**: Efficiently scrapes articles across multiple pages.
- **Category-wise Data Storage**: News articles are stored in separate JSON files for each category.
- **Scalability**: Can be extended to scrape additional information such as article content, author names, and timestamps.

## Installation

This project requires Python 3 and Scrapy.

### Install Scrapy

```sh
pip install scrapy
```

### Clone the Repository

```sh
git clone https://github.com/deepanshum0408/Web-scraping-using-Scrapy
cd Web-scraping-using-Scrapy
```

## Usage

To start scraping, navigate to the project directory and run the following command:

```sh
scrapy crawl buis -o business_news.json
```

This command will run the spider and store the extracted data in `business_news.json`. You can modify the spider to scrape other categories.

### Example Scraper Code

```python
import scrapy

class NewsSpider(scrapy.Spider):
    name = 'buis'
    start_urls = ['https://assam.nenow.in/category/business/']

    def parse(self, response):
        for article in response.css('div.jeg_postblock_content'):
            yield {
                'title': article.css('h3.jeg_post_title a::text').get(),
            }
        
        pagination_links = response.css('a.page_number::attr(href)').getall()
        for link in pagination_links:
            yield scrapy.Request(response.urljoin(link), callback=self.parse)
```

## Output Format

The scraped data is stored in JSON format with the following structure:

```json
[
    {
        "title": "Sample News Title 1"
    },
    {
        "title": "Sample News Title 2"
    }
]
```

<h2 id="contact">Contact</h2>
  <p>For any inquiries or feedback, please contact:</p>
  <ul>
    <li><strong>Name:</strong> Deepanshu Miglani</li>
    <li><strong>Education:</strong> B.tech CSE(AIML) , UPES, Dehradun</li>
    <li><strong>Email:</strong> deepanshumiglani0408@gmail.com / Deepanshu.106264@stu.upes.ac.in</li>
    <li><strong>GitHub:</strong> <a href="https://github.com/deepanshum0408">deepanshum0408</a></li>
  </ul>
  
  <h2 id="mentor">Mentor</h2>
  <p><strong>Dr. Sahinur Rahman Laskar</strong><br>
  Assistant Professor<br>
  School of Computer Science, UPES, Dehradun, India<br>
  Email: sahinurlaskar.nits@gmail.com / sahinur.laskar@ddn.upes.ac.in<br>
  </p>
