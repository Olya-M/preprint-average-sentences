# Preprint average sentences
This is a tool with a graphical user interface that scrapes groups of articles from biorxiv or medrxiv searches, sumarrizes the articles by outputting the average sentences for each paragraph in each preprint, and clusters the articles based on the most average sentences. I made this when I wanted there to be a quick way to catch up on any new biomed topic.
 
Lazy way to read up on a topic
Abstractive summarization avoided*

### Webscraping
done with BeautifulSoup

HuggingFace

### Summarization method
This notebook uses a simple version of extractive summarization. It cuts out text
Used **(https://www.sbert.net/docs/pretrained_models.html)

[all-mpnet-base-v2](https://www.sbert.net/docs/pretrained_models.html)

**pretrained model ***

I tried out abstractive summarization methods including Pegasus, but I found that there was too much hallucination
I initially wanted to add an abstractive summarization method with a pretrained e.g. [Pegasus](https://huggingface.co/transformers/model_doc/pegasus.html) model but I ran into the problem of text hallucination (i.e. the model coming up with unreliable text that's not in the content being summarized). 

### Clustering


### GUI
The GUI is built with [tkinter](https://tkdocs.com/). 
tkinter

### Usage
If you would like to use this notebook you will need to first install all of the dependencies for the first cell. Then, download the model weights (418mb) by running the second cell before running the rest of the cells. The GUI will pop up after running the final cell. Folders for "scraped_texts" and "processed_texts" will pop up in the same directory as the notebook during text scraping and processing. The whole process can take 5-10 min per 100 articles.
