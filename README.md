# Basic Web Crawler

This publication consists on the crawling pipeline developed during the course 'Statistcal Methods for Text Data Analysis' offered in Tampere University. This chosen functions show the logic of a well implemented web crawler, that can be used for different other crawling projects.

## Table of contents

- [Short description](https://github.com/robredomikel/basic-web-crawler#short-description)
- [What each function does](https://github.com/robredomikel/basic-web-crawler#what-each-function-does)
        - [webCrawler](https://github.com/robredomikel/basic-web-crawler#webcrawler)
        - [gettextlist](https://github.com/robredomikel/basic-web-crawler#gettextlist)
        - [filecrawler](https://github.com/robredomikel/basic-web-crawler#filecrawler)
- [Necessary libraries](https://github.com/robredomikel/basic-web-crawler#necessary-libraries)
- [Short note about preprocessing each text](https://github.com/robredomikel/basic-web-crawler#short-note-about-preprocessing-each-text)
- [References](https://github.com/robredomikel/basic-web-crawler#references)

## Short description

Our task was to create a pipeline that would browse into [Project Gutenberg](https://www.gutenberg.org) webpage and would move to the [Top downloaded 100 EBooks last 7 days](https://www.gutenberg.org/browse/scores/top#books-last30). Then, it would download the amount of wanted ebooks starting from the most downloaded one and move into ascending order into a local directory, fetch all of them one by one and store them into a list, in order to manipulate or work with them.

## What each function does

### webCrawler
Takes as parameters the amount of ebooks to be downloaded and the initial webpage in which we start crawling. In the first stage the function parses the initial webpage for the link extentions of the ebooks to be downloaded and stores them in a list.
Then, for each link extension a new link with the address to the book txt file will be created by merging the extention with the original url link. Through this link, we request the content and store it as a txt file in our local directory.
### gettextlist
Goes through all the content of the local directory in order to classify each tipe of content object. For that it gets the full local path for each content and check whether is file or not, and if it is, then it classifies if the file is of text type or not. This function is used in the "filecrawler" function.
### filecrawler
This function works for cleaning the text files. In this way, through the "gettextlist" function obtains three different lists of text files, non-text files and non-files, and from the first group, processes each text file by cleaning parts of the texts that shouldn't be considered in the tasks to be done. (e.g. headers of an email, headers or footers of a book...)
## Necessary libraries
To compute this functions, Python offers different libraries that can help the process to be done:
- **os:** Used to join initial url addresses with the extentions for each document web address.
- **requests:** Gets the content of the webpage requested.
- **bs4:** Web parser, used in order to pull information from HTML files.
## Short note about preprocessing each text
This preprocessing pipeline is not meant to be universal but just give a hint on how to fetch specific content for a specific task in a standarised approach, which for me was downloading several ebooks to perform statistical methods on them.
## References
- [Statistical Methods for Text Data Analysis - Tampere University](https://www.tuni.fi/en/study-with-us/statistical-methods-text-data-analysis-lectures#url-controlled-expander-trigger--study-program-non-degree-368009) 
- [Beautiful Soup library](https://beautiful-soup-4.readthedocs.io/en/latest/)
- [os — Miscellaneous operating system interfaces — Python 3.11.1 documentation](https://docs.python.org/3/library/os.html)
- [Python’s Requests Library (Guide) – Real Python](https://realpython.com/python-requests/)
