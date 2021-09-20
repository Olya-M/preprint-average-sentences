# Preprint average sentences
This is a tool with a graphical user interface that scrapes groups of articles from biorxiv or medrxiv searches, sumarrizes the articles by outputting the average sentences for each paragraph in each preprint, and clusters the articles based on the most average sentences. I made this when I wanted there to be a quick way to catch up on any new biomed topic. The webscraping is done with [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)

### Webscraping
done with BeautifulSoup

HuggingFace

### Summarization method
This notebook uses a simple version of extractive summarization; it cuts out and returns the most relevant text in an article. I chose most relevant by which sentence had the most average sentence embedding for each paragraph. Sentence embeddings are generated with a pretrained BERT model, and the most average sentence per paragraph is found by cosine similarity to an averaged-out paragraph embedding.
Used **(https://www.sbert.net/docs/pretrained_models.html)

[all-mpnet-base-v2](https://www.sbert.net/docs/pretrained_models.html)

**pretrained model ***

I tried out abstractive summarization methods including Pegasus, but I found that there was too much hallucination
I initially wanted to add abstractive summarization with a pretrained e.g. [Pegasus](https://huggingface.co/transformers/model_doc/pegasus.html) model but I ran into the problem of text hallucination (i.e. the model coming up with unreliable text that's not in the content being summarized). 

### Clustering
For clustering, most average sentence per article
Automatic elbow method** not great maybe
Then shows keywords for each cluster

### GUI
The GUI is built with [tkinter](https://tkdocs.com/). 
tkinter

### Usage
If you would like to use this notebook you will need to first install all of the dependencies for the first cell. Then, download the model weights (418mb) by running the second cell before running the rest of the cells. The GUI will pop up after running the final cell. Folders for "scraped_texts" and "processed_texts" will pop up in the same directory as the notebook during text scraping and processing. The whole process can take 5-10 min per 100 articles.
