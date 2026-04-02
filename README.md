# AI-Search

[![AI-Search py (1)](https://raw.githubusercontent.com/oxylabs/oxylabs-ai-studio-js/refs/heads/main/images/Github-AI-Studio-1262x525px%20new.png)](https://aistudio.oxylabs.io/?utm_source=877&utm_medium=affiliate&utm_campaign=ai_studio&groupid=877&utm_content=ai-search-py-github&transaction_id=102f49063ab94276ae8f116d224b67) 

[![](https://dcbadge.limes.pink/api/server/Pds3gBmKMH?style=for-the-badge&theme=discord)](https://discord.gg/Pds3gBmKMH) [![YouTube](https://img.shields.io/badge/YouTube-Oxylabs-red?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@oxylabs)

The [**AI-Search**](https://aistudio.oxylabs.io/apps/search) app by [**Oxylabs AI Studio**](https://aistudio.oxylabs.io/) is a web search tool that allows developers to retrieve search results, optionally scrape them, and handle JavaScript-rendered content with ease. It is built to act as an intelligent search agent that simplifies the process of extracting relevant information directly into your Python applications.

Whether you need a simple list of URLs or deep content extraction, AI Search removes the complexity of building custom search scrapers from scratch.

## Key features

- **Query web using plain English:** Simply provide your search query in natural language and let the agent do the heavy lifting.
- **Control number of search results:** Easily define exactly how many results you want to retrieve.
- **Optional content scraping for result pages:** Automatically scrape and extract content snippets directly from the returned search results.
- **Python rendering for dynamic content:** Enable rendering to seamlessly handle and extract data from JavaScript-heavy websites.

## How it works

To use the search agent, follow these simple steps:
1. **Input the search query** you want to look up.
2. **Set the desired number of results** to limit or expand your search scope.
3. **Toggle content scraping and JS rendering** based on whether you need deep content extraction or just URLs and titles.

### Installation

TTo begin, be sure you have access to an API key (or [get a free trial](https://aistudio.oxylabs.io/register) with **1,000 credits**) and `Python 3.10+` installed. You can install the oxylabs-ai-studio package using pip:

```bash
pip install oxylabs-ai-studio
```

### Code examples (Python)

The following example demonstrates how to use the `AI-Seaerch` agent for data retrieval scenarios.

```python
from oxylabs_ai_studio.apps.ai_search import AiSearch

search = AiSearch(api_key="<API_KEY>")

query = "lasagna recipes"
result = search.search(
    query=query,
    limit=5,
    render_javascript=False,
    return_content=True,
)
print(result.data)
```
Learn more about AI-Search and Oxylabs AI Studio Python SDK in our [PyPI repository](https://pypi.org/project/oxylabs-ai-studio/). You can also check out our [AI Studio JavaScript SDK](https://github.com/oxylabs/oxylabs-ai-studio-js) guide for JS users.


### Request Parameters

| Parameter            | Description                                         | Default Value |
|----------------------|-----------------------------------------------------|---------------|
| `query`              | What to search for                                  | **Required**  |
| `limit`              | Maximum number of results to return (Maximum: 50)   |  10           |
| `render_javascript` | Output format (`json`, `markdown`)                   | `False`       |
| `render_javascript` | Enable render JavaScript                             | `False`       |
| `return_content`    | Whether to return markdown contents in results       | `True`        |
| `geo_location`      | Proxy location in ISO2 format                        |   –           |

**Note:** When `limit <= 10` and `return_content=False`, the search automatically uses the instant endpoint (`/search/instant`) which returns results immediately without polling, providing faster response times.


### Output Sample

```python
[
  {
    "url": "https://www.spendwithpennies.com/easy-homemade-lasagna/",
    "title": "Easy Homemade Lasagna Recipe - Spend With Pennies",
    "description": "Rating 5.0 (3,349) · 1 hr 45 min This is the best LASAGNA RECIPE! Pasta, an easy meat sauce, and ricotta cheese are layered and then topped with more cheese before baking.",
    "content": null
  },
  {
    "url": "https://www.simplyrecipes.com/recipes/lasagna/",
    "title": "The Best Homemade Lasagna - Simply Recipes",
    "description": "Rating 4.9 (115) · 1 hr 45 min This classic lasagna recipe is made with an easy meat sauce as the base. Layer the sauce with noodles and cheese, then bake until bubbly!",
    "content": null
  },
  {
    "url": "https://www.seriouseats.com/12-lasagna-recipes-11808722",
    "title": "12 Must-Try Lasagna Recipes Featuring Crispy Edges and Gooey ...",
    "description": "Whether you have a taste for meaty classics like a lasagna alla Bolognese or an indulgent creamy vegetarian spinach lasagna, we've rounded up our favorite ...",
    "content": null
  },
  {
    "url": "https://bakerbynature.com/the-best-homemade-lasagna-recipe/",
    "title": "The Best Easy Homemade Lasagna Recipe - Baker by Nature",
    "description": "Rating 5.0 (71) · 2 hr 45 min Dec 12, 2025 · This is the ONLY lasagna recipe you'll ever need... from perfectly cooked noodles to rich tomato sauce and layers of cheese.",
    "content": null
  },
  {
    "url": "https://www.allrecipes.com/recipe/23600/worlds-best-lasagna/",
    "title": "World's Best Lasagna Recipe (with Video) - Allrecipes",
    "description": "Rating 4.8 (20,950) · 3 hr 15 min Feb 5, 2026 · This lasagna recipe from John Chandler is our most popular recipe! With sausage, ground beef, basil, and 3 types of cheese, it lives up to ...",
    "content": null
  }
]
```

## Practical use cases

AI-Search can be applied to a wide variety of data discovery and collection tasks:

1. **Search for latest news or articles on a topic –** Quickly gather up-to-date information, headlines, and summaries.
2. **Discover books, movies, or products –** Retrieve lists of items matching specific criteria or reviews.
3. **Research competitive offerings –** Find and analyze competitor pricing, features, and market positioning.
4. **Aggregate industry updates from multiple sites –** Compile relevant industry changes and trends into a single, structured feed.

## FAQ

### 1. How do I get faster search results if I only need URLs and titles?
If you don't need to extract the full page content, you can use the `instant_search` method (as shown in the first example) or set `return_content=False` in the standard search method. This bypasses the deep scraping process and returns your search results almost instantly.

### 2. Can I get search results from a specific country or location?
Yes, you can use the geo_location parameter to localize your search results. It supports ISO 2-letter country codes (e.g., `US`, `DE`), full country canonical names, or specific geographic coordinates, allowing you to see exactly what users in that region see.

### 3. Why am I not getting the full content from certain websites?
Some modern websites rely heavily on JavaScript to load their content dynamically (like Single Page Applications). If the returned content snippet is empty or missing data, try setting `render_javascript=True` in your request. This tells the search agent to fully render the page like a real browser before extracting the text.

### 4. What is the maximum number of search results I can retrieve at once?
You can retrieve up to 50 search results per query by adjusting the limit parameter. If you do not specify a limit, the search agent will return 10 results by default.


## Learn more
For a deeper dive into available parameters, advanced integrations, and additional examples, check out the [AI Studio documentation](https://aistudio.oxylabs.io/apps/search).

## Contact us
If you have questions or need support, reach out to us at [hello@oxylabs.io](mailto:hello@oxylabs.io) or through [live chat](https://oxylabs.drift.click/oxybot).
