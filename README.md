# Preprint average sentences
This is a tool with a graphical user interface that scrapes groups of articles from biorxiv or medrxiv searches, sumarrizes the articles by outputting the average sentences for each paragraph in each preprint, and clusters the articles based on the most average sentences. I made this when I wanted there to be a quick way to catch up on any new biomed topic. 

#### In-use example:
![eg search 1](https://user-images.githubusercontent.com/68296887/134078645-c7ba8a72-aa70-48fe-9894-8d5b3489ad4f.png)

![eg search 2](https://user-images.githubusercontent.com/68296887/134078656-af488441-df05-4382-a1cd-7ae4a012a2ce.png)

![eg search 3](https://user-images.githubusercontent.com/68296887/134078745-c929c9e6-8c2d-4467-b340-1abe916b6120.png)




The webscraping is done with [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/). Sentences embedding is done with an [all-mpnet-base-v2 pretrained sentence-transformers model](https://huggingface.co/sentence-transformers/stsb-mpnet-base-v2) downloaded via Hugging Face, average sentences are found via cosine similarity, and clustering is done with k-means clustering the sentence embeddings for the most average sentence per text. An automatic elbow method is used to choose the number of clusters. For each cluster, five keywords are returned. The GUI is built with [tkinter](https://tkdocs.com/). 


### Summarization method
This notebook uses a simple version of extractive summarization; it cuts out and returns the most relevant text in an article. One sentence is returned per paragraph based on the highest cosine similarity to an averaged-out paragraph embedding.
Used **(https://www.sbert.net/docs/pretrained_models.html)

[all-mpnet-base-v2](https://www.sbert.net/docs/pretrained_models.html)

**pretrained model ***

I tried out pretrained [Pegasus](https://huggingface.co/transformers/model_doc/pegasus.html) models to add some abstractive summarization but I found that there was too much text hallucination (i.e. the model outputting unreliable text that's not from the content being summarized).

### Usage
If you would like to use this notebook you will need to first install all of the dependencies for the first cell. Then, download the model weights (418mb) by running the second cell before running the rest of the cells. The GUI will pop up after running the final cell. Folders for "scraped_texts" and "processed_texts" will pop up in the same directory as the notebook during text scraping and processing. The whole process can take 5-10 min per 100 articles.
