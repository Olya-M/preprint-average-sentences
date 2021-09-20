# Preprint average sentences
This is a tool with a graphical user interface that scrapes groups of articles from biorxiv or medrxiv searches, outputs the average sentences for each preprint, and clusters the articles based on the most average sentences. I made this when I wanted there to be a quick way to catch up on any new biomed topic.
 
Lazy way to read up on a topic
Abstractive summarization avoided*

### Webscraping
done with BeautifulSoup

HuggingFace

### Summarization method
I tried out abstractive summarization methods including Pegasus, but I found that there was too much hallucination

### Clustering


### GUI
The GUI is built with [tkinter](https://tkdocs.com/). 
tkinter

### Usage
To use this notebook, install all of the dependencies for the first cell and download the model weights in the second cell. Then, run the rest of the cells. The GUI will pop up after running the final cell. Folders for "scraped_texts" and "processed_texts" will pop up in the same directory as the notebook during text scraping and processing.
