# Preprint average sentences
This is a tool with a graphical user interface that scrapes groups of articles from biorxiv or medrxiv searches, sumarrizes the articles by outputting the average sentences for each paragraph in each preprint, and clusters the articles based on the most average sentences. I made this when I wanted there to be a quick way to catch up on any new biomed topic. 

#### In-use examples:
![eg search 1](https://user-images.githubusercontent.com/68296887/134075228-33a31253-a1bf-4d98-bc12-0c17ba52653f.png)

![eg search 2](https://user-images.githubusercontent.com/68296887/134075237-9d33dc76-9c88-4117-82f1-898218a2547e.png)

![eg search 3](https://user-images.githubusercontent.com/68296887/134078227-5f0a076b-9e5d-4428-b5d6-2c1f2c81ad60.png)

The webscraping is done with [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/). Sentences embedding is done with an [all-mpnet-base-v2 pretrained sentence-transformers model](https://huggingface.co/sentence-transformers/stsb-mpnet-base-v2) downloaded via Hugging Face, average sentences are found via cosine similarity, and clustering is done with k-means clustering the sentence embeddings for the most average sentence per text. An automatic elbow method is used to choose the number of clusters. For each cluster, five keywords are returned. The GUI is built with [tkinter](https://tkdocs.com/). 


### Summarization method
This notebook uses a simple version of extractive summarization; it cuts out and returns the most relevant text in an article. One sentence is returned per paragraph based on the highest cosine similarity to an averaged-out paragraph embedding.
Used **(https://www.sbert.net/docs/pretrained_models.html)

[all-mpnet-base-v2](https://www.sbert.net/docs/pretrained_models.html)

**pretrained model ***

I tried out pretrained [Pegasus](https://huggingface.co/transformers/model_doc/pegasus.html) models to add some abstractive summarization but I found that there was too much text hallucination (i.e. the model outputting unreliable text that's not from the content being summarized).

### Usage
If you would like to use this notebook you will need to first install all of the dependencies for the first cell. Then, download the model weights (418mb) by running the second cell before running the rest of the cells. The GUI will pop up after running the final cell. Folders for "scraped_texts" and "processed_texts" will pop up in the same directory as the notebook during text scraping and processing. The whole process can take 5-10 min per 100 articles.
