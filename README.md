
# Unsupervised_Web_Extraction

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
This section should contain a detailed description of all different components and models that you will be using to achieve your task as well as a diagram. Here is a very basic example of what you should include:

We generate vector representations for each document using BERT, we then train a simple, single-layer fully connected neural network using the documents and labels from the training set.

First, we select a set of labeled text documents `d_1, d_2, …, d_N` from the arxiv dataset available on Kaggle. The documents are randomly partitioned into two sets for training and testing. We use the BERT language model's output as the input to the neural network. Only the weights of the neural network are modified during training. 

After training, we run the trained model to classify the test documents into one of the classes in C. Below is a picture of the architecture of the module. The diagram below was constructed using draw.io 


![design architecture](https://github.com/Forward-UIUC-2021F/guidelines/blob/main/template_diagrams/sample-design.png)





## Issues and Future Work

In this section, please list all know issues, limitations, and possible areas for future improvement. For example:

* High false negative rate for document classier. 
* Over 10 min run time for one page text.
* Replace linear text search with a more efficient text indexing library (such as whoosh)
* Include an extra label of "no class" if all confidence scores low. 
