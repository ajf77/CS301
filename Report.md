# CS 301 Project Report

# Q&A System with Natural Language Processing


## Abstract

The problem that is to be solved is the ability for a given natural question to be answered using natural language. More specifically, a question in a given natural language is to be given an answer. The method by which this problem will be solved is by first interpreting the natural language question, and then searching for the answer using an existing dataset, otherwise known as a longform Q&A system. In this instance, I will be using the Haystack NLP framework. This framework allows for database entries to be inputted, giving items to be used for searching. Natural language questions can then be inputted into the framework. Certain parameters of Haystack can also be modified to help refine the search and retrieve more accurate results. The more accurate the desired results, the longer it will take to retrieve them.

## Introduction

The problem to solve for this project is to create a system for longform Q&A. There will be a question asked by a user in natural language. This question will then be interpreted by the pipeline, which will allow for it to be able to find an answer. The answer that is retrieved will have come from documents that were fed into the pipeline to give it data. In this instance, the data will be coming from wikipedia.

## Related Work
Several companies have begun to implement longform Q&A systems of their own. One such company is facebook. Their pipeline is very similar to the Haystack pipeline, and it works the same way. The pipeline takes in questions asked in natural languages, and then is able to interpret these questions and then produce an answer. The answers that the pipeline is able to produce is dependent on the documents of information that is provided for the pipeline. In the case of facebook, they used information on the public subreddit “Explain Like I’m Five”. The answers given by the pipeline can both be either extractive or abstract. An abstract answer is a natural sounding answer that the program attempts to create. An extractive answer is one taken straight from the stored documents. 

## Data

The data I used was 20 articles about selected video games. All articles were downloaded using the wikipedia python module. This is the list of games used:

Longform Q&A systems are important because they allow people to be able to search for information more easily, as well as in less time. Since the system is able to recognize and interpret information given in natural language, it allows for a user to be able to ask a simple question and then immediately get an answer. This is also much quicker, as all the user has to do to search is type in a question, as opposed to having to search through large amounts of text. 

## Methods

The first thing that needs to be done is to download all the wikipedia articles. I did this by using the wikipedia module in python to reference the articles and then I stored them all in a DocumentStore. The DocumentStore being used is ElasticSearch, and is mainly used to store documents to be used for search. ElasticSearch is one of multiple options that could be used as a DocumentStore for Haystack, the other options being FAISS and Mulvus. 

Haystack can be broken down into several different parts, the retriever, reader, summarizer, and generator. The retriever is what retrieves relevant information from the database to be used in giving an answer for search. The reader is what narrows the search down from the information from the retriever. The summarizer takes information from the natural language question and uses it to summarize an answer based on the documents. The generator uses the information from the documents to make a concise answer. These parts all work together to help to return an accurate answer and in the way that the user wants to see it.

The ExtractiveQA pipeline is the part of Haystack that utilizes the retriever, reader, as well as interprets the question. When the question is asked in Haystack, the ExtractiveQA pipeline takes the question as input, uses the retriever to retrieve information, and then reads the information given by the retriever. The output is the final result in the form of natural language.

The purpose of the retriever is to narrow down the field of possible results for the given natural language question. It does this using the given information from the DocumentStore to find words that match the ones from the question. If the words match, it will send that part of a document to the next step. The purpose of this is to efficiently narrow down the search field for the final answer. This will help the reader to more effectively be able to find the correct answer it is looking for.

The purpose of the reader is to precisely read the information from the documents that was inputted into the DocumentStore. The information from the DocumentStore that it ends up reading is the information that was interpreted by the retriever. The reader is able to narrow down the information even further to be able to yield the result that answers the natural language question. Once it finds the answer, it will output it.

## Experiments
For my experiment I wanted to see the difference in results if I modified the precision of the retriever. This can be done by modifying the top_k parameter when running the pipeline. The higher the number, the more precise the result will be. However, this also will cause the results to take much longer to process. This is most likely due to the fact that the retriever is analyzing the documents much more closely. In order to see the differences, I ran the program 3 different times. Once with the top_k parameter set to its default value(10), another time with it set to 20, and another time with it set to 5. Each result yielded something a bit different. 

The first two, while they yielded the exact same results, the second one took much longer to complete.

top_k=10

## Conclusion
To conclude, I have learned that Longform Q&A systems have advanced to the point that they can accurately answer different forms of natural language questions. Haystack is a good example of how powerful and useful Longform Q&A can be.  Exploring the features of Haystack, it can be seen how simple it is to allow the question pipeline to take in a question and then be able to produce an answer just by providing data. Haystack also shows that it can return an answer that is also in natural language, allowing for users to be able to ask questions and get answers without any technical knowledge.

In the future, if I had more time, I would explore different and more advanced datasets. In doing so, I would hope to further my knowledge on the subject of how haystack interprets its answers, as well as what types of questions are harder for it to answer. In doing so, I hope to greater understand how we can make improvements in the future, such as allowing for more efficient search as well as allowing for a more broad range of questions that are able to be asked.

## References

deepset-ai Haystack. https://github.com/deepset-ai/haystack

Introducing long-form question answering. Jernite, Y., Fan, A., and Auli, M. Towards Data Science https://ai.facebook.com/blog/longform-qa/

Transformers. Kulshresthra, R. Towards Data Science. https://towardsdatascience.com/transformers-89034557de14
