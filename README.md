
p align="center">
<a href="https://trendshift.io/repositories/9761" target="_blank"><img src="https://trendshift.io/api/badge/repositories/9761" alt="VinciGit00%2FScrapegraph-ai | Trendshift" style="width: 250px; height: 55px;" width="250" height="55"/></a>
<p align="center">

[ScrapeGraphAI](https://scrapegraphai.com) is a *web scraping* python library that uses LLM and direct graph logic to create scraping pipelines for websites and local documents (XML, HTML, JSON, Markdown, etc.).

Just say which information you want to extract and the library will do it for you!

<p align="center">
</p>

## 🔗 ScrapeGraph API & SDKs

<p align="center">
</p>

We offer SDKs in both Python and Node.js, making it easy to integrate into your projects. Check them out below:

| SDK       | Language | GitHub Link                                                                 |
|-----------|----------|-----------------------------------------------------------------------------|


## 🚀 Quick install


```bash
pip install scrapegraphai

playwright install
```

**Note**: it is recommended to install the library in a virtual environment to avoid conflicts with other libraries 🐱

<details>
<summary><b>Optional Dependencies</b></summary>
Additional dependecies can be added while installing the library:

- <b>More Language Models</b>: additional language models are installed, such as Fireworks, Groq, Anthropic, Hugging Face, and Nvidia AI Endpoints.

  This group allows you to use additional language models like Fireworks, Groq, Anthropic, Together AI, Hugging Face, and Nvidia AI Endpoints.
  ```bash
  pip install scrapegraphai[other-language-models]
  ```
- <b>Semantic Options</b>: this group includes tools for advanced semantic processing, such as Graphviz.

  ```bash
  pip install scrapegraphai[more-semantic-options]
  ```

- <b>Browsers Options</b>: this group includes additional browser management tools/services, such as Browserbase.

  ```bash
  pip install scrapegraphai[more-browser-options]
  ```

</details>


## 💻 Usage
There are multiple standard scraping pipelines that can be used to extract information from a website (or local file).

The most common one is the `SmartScraperGraph`, which extracts information from a single page given a user prompt and a source URL.


```python
import json
from scrapegraphai.graphs import SmartScraperGraph

# Define the configuration for the scraping pipeline
graph_config = {
    "llm": {
        "api_key": "YOUR_OPENAI_APIKEY",
        "model": "openai/gpt-4o-mini",
    },
    "verbose": True,
    "headless": False,
}

# Create the SmartScraperGraph instance
smart_scraper_graph = SmartScraperGraph(
    prompt="Extract me all the news from the website",
    source="https://www.wired.com",
    config=graph_config
)

# Run the pipeline
result = smart_scraper_graph.run()
print(json.dumps(result, indent=4))
```

The output will be a dictionary like the following:

```
There are other pipelines that can be used to extract information from multiple pages, generate Python scripts, or even generate audio files.

| Pipeline Name           | Description                                                                                                      |
|-------------------------|------------------------------------------------------------------------------------------------------------------|
| SmartScraperGraph       | Single-page scraper that only needs a user prompt and an input source.                                           |
| SearchGraph             | Multi-page scraper that extracts information from the top n search results of a search engine.                  |
| SpeechGraph             | Single-page scraper that extracts information from a website and generates an audio file.                       |
| ScriptCreatorGraph      | Single-page scraper that extracts information from a website and generates a Python script.                     |
| SmartScraperMultiGraph  | Multi-page scraper that extracts information from multiple pages given a single prompt and a list of sources.    |
| ScriptCreatorMultiGraph | Multi-page scraper that generates a Python script for extracting information from multiple pages and sources.     |

For each of these graphs there is the multi version. It allows to make calls of the LLM in parallel.

It is possible to use different LLM through APIs, such as **OpenAI**, **Groq**, **Azure** and **Gemini**, or local models using **Ollama**.

Remember to have [Ollama](https://ollama.com/) installed and download the models using the **ollama pull** command, if you want to use local models.

## 🔍 Demo
Official streamlit demo:
