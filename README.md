
# unsupervised_web_extraction

## Overview

This project goes over different ways of doing mostly unsupervised web information extraction from a set of similar webpages. 

This repo was used mostly for exploration so I recommend to use this Google collab that presents the approaches used in a easier to read fashion.
[Open in Google Colab](https://colab.research.google.com/drive/1Ax4yyOa1avfro1PjNmitcrQPD4Q3HHLt?usp=sharing)



  
Week1_tasks: This shows the The Manuel Extraction Method and Google Query Method.
  
Week2_tasks: This shows some improvement in The Manuel Extraction Method as well as some exploration of unsupervised methods that didn't bear many fruits.
  
Week3_tasks: This shows the ability of The Manuel Extraction Method to get Chemistry Professor pages as well as Computer Science Professor pages, and the Clusterting Approach.
  
Week4_tasks: This shows learning on how to use xpaths for extracting information.
  
Week5_tasks: This shows The Roadrunner Approach that is ommited because of size. It was mostly looking through this repo which you can explore- https://github.com/roberttovornik/webpage-data-extraction
  
Week6_tasks: This shows what the ChatGpt progam could like using the API for information extraction, and differnt ways of trying to shrink the webpage text to go into the prompt size using a summarizer. 

## Setup

The steps needed to install your module's dependencies: 

Python Version 3.9 is used and pip Version 23.0
```
pip install -r requirements.txt 
```



```
├── Week1_tasks
│   ├── data_mining_t1.ipynb
│   ├── google_search_mining.ipynb
│   ├── people.txt
│   ├── people2.txt
│   └── textrank.txt
├── Week2_tasks
│   ├── data_mining_t2.ipynb
│   ├── people.csv
│   └── people.txt
├── Week3_tasks
│   ├── data_mining_t3.ipynb
│   ├── people.txt
│   └── simple_dom_paper_imp.ipynb
├── Week4_tasks
│   └── data_mining_t4.ipynb
├── Week6_tasks
│   ├── data_mining_t6.ipynb
│   └── output.txt
└── requirements.txt

6 directories, 15 files
```


### Important 
Go to [our shared google Drive space](https://drive.google.com/drive/folders/1rxPAdGTVcl-Xo6uuFovdKcCw5_FEaXIC?usp=sharing) and create a folder with the format `FirstnameLastName-Projectname` (e.g. `AshutoshUkey-KeywordTrie`). In here, make sure to include a zipped copy of any data files related to your module (including `.sql` dumps of necessary databases) as well as a backup zipped copy of your Github repo (i.e. all the files you upload to Github).


## Demo video
Make sure to include a video showing your module in action and how to use it in this section. Github Pages doesn't support this so I am unable to do this here. However, this can be done in your README.md files of your own repo. Follow instructions [here](https://stackoverflow.com/questions/4279611/how-to-embed-a-video-into-github-readme-md) of the accepted answer 


## Algorithmic Design 

**For Approach 1: Manuel Extraction**:

1. The script imports necessary libraries, such as requests and BeautifulSoup, for making HTTP requests and parsing HTML content.

2. The script defines several helper functions:

extract_title function extracts the name, department, and university from the HTML content of a webpage.
extract_contact_info function extracts email, phone, and office information from the webpage.
extract_list_info function extracts information organized in lists from the webpage.
extract_person_info function combines the above functions to extract various pieces of information about a person from their webpage.
write_person_info function writes the extracted person information to a file.

3. The script defines a list of headers that specify the sections to extract from the professor's webpage.

4. The process_prof function takes a professor's name, URL, and headers as input. It calls extract_person_info to extract the information and then writes it to a file using write_person_info.

5. The run_extraction function takes a list of professors, a base URL, and headers as input. It creates a thread pool executor to concurrently process each professor's webpage using the process_prof function.

6. The script provides two examples of running the extraction process:

The first example scrapes information about computer science professors from the given URL (https://cs.illinois.edu/about/people/all-faculty/) for the professors listed in cs_profs.
The second example scrapes information about chemistry professors from the given URL (https://chemistry.illinois.edu/) for the professors listed in chem_profs. 

___

**For Approach 2: Google Query Method**:

The provided code creates a Python script that generates a word cloud based on a Google search for a given professor's name. Here's a breakdown of the code:

1. The script imports necessary libraries such as requests, BeautifulSoup, WordCloud, matplotlib.pyplot, and nltk. These libraries are used for making HTTP requests, parsing HTML content, generating word clouds, and performing text processing tasks.

2. The script prompts the user to enter a professor's name using the input function and stores it in the search_query variable.

3. The script constructs a URL by appending the search_query to a Google search URL.

4. The script sends a GET request to the constructed URL and retrieves the HTML content of the search results page.

5. The script uses BeautifulSoup to parse the HTML content and extract the text from it. The stripped_strings method is called on the soup object to get all the text elements without the surrounding tags.

6. The script tokenizes the extracted text using the nltk.word_tokenize function, which splits the text into individual words or tokens.

7. It removes stop words, which are common words like "the," "is," and "and," using the nltk.corpus.stopwords module. The script converts all the tokens to lowercase and checks if they are present in the set of stop words. If not, they are added to the filtered_tokens list.

8. The script calculates the frequencies of the filtered tokens using the nltk.FreqDist function and stores them in the freq_dist object.
It creates a dictionary, word_freq, to store the word frequencies as key-value pairs.

___

**For Approach 3: Clustering Approach**:

1. The script sends a GET request to a specific webpage (in this case, the webpage for a faculty member at the University of Illinois at Urbana-Champaign). The response content is stored in the html_content variable.
The script uses BeautifulSoup to parse the HTML content and create a BeautifulSoup object named soup.

2. The script extracts the text from the header elements on the webpage using regular expressions. It finds all the header elements that start with 'h' followed by a digit (e.g., h1, h2, etc.) and appends the stripped text to the header_text list.

3. The script uses the CountVectorizer class from scikit-learn to convert the header_text list into a document-term matrix. The stop_words parameter is set to 'english' to remove common English words from the analysis.

4. It applies K-means clustering to the document-term matrix. The variable k determines the number of clusters to create. The script initializes the KMeans object with the specified parameters and fits the data using the fit method.

5. The script prints the cluster labels for each header. It assigns the labels to the labels variable using the labels_ attribute of the fitted KMeans object. It then iterates over the range of cluster indices and prints the cluster number along with the headers associated with that cluster.

___

**For Approach 5: ChatGPT Method**:

1. This Method does not have code but uses Chatgpt's Interface to extract the Information by putting the text of the webpage into the prompt.

For example using the prompt in [Google Colab](https://colab.research.google.com/drive/1Ax4yyOa1avfro1PjNmitcrQPD4Q3HHLt?usp=sharing):
You should get a similar output in JSON format:
{ "name": "Jeff Erickson", "education": [ { "degree": "Ph.D.", "field": "Computer Science", "university": "University of California, Berkeley", "date": "July 1996" }, { "degree": "M.S.", "field": "Information and Computer Science", "university": "University of California, Irvine", "date": "June 1992" }, { "degree": "B.A.", "field": "Computer Science and Mathematical Sciences", "university": "Rice University", "date": "May 1987" } ], "research interests": [ "Algorithms", "data structures, and lower bounds", "Computational and discrete geometry and topology" ], "phone number": "(217) 333-6769" }




## Issues and Future Work

Approach 2: Google Query Method: The data gotten from the webpages text has a very high noise ratio of mostly irrrelvant information or symbols which makes searching for more webpages not anymore helpful than less pages usually.

Approach 3: Clustering Approach: This was a early attempt at trying to do unsupervised web extraction and the results warrent it to not be used for anything serious given the poor results.

Approach 4: RoadRunner Ommited: The github repo explored had some problems with different types of inputs from pages not included in its samples. 

Approach 5: ChatGpt Method: Paid Api which makes it running it not through the UI an expensive option for many webpages for extraction. Also if you don't give it enough webpage text information it will make up information to fill out the JSON output.

Approach 6: OpenSource LLM Method: Some models have poor results in comparsion to ChatGPT. Also running the models locally takes lots of compute power for models that have a chance to get results similar to ChatGpt and smaller models don't show promosing results. 

