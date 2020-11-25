# Scholarly Recommender

This project is called the Scholarly Data Recommender, and it is a recommender system model in the form of a search engine where if a user inputs a keyword, it will pull scholarly data from the National Center for Biotechnology Information, recommends several documents that are the most relevant to the keyword, and then provides extra analytics on the scholarly network so that the user can further expand their research.

First, I should explain a bit on what scholarly data is.
Normally, the data we work with is solely related to our individual projects.

However, "scholarly" data is a term created recently for databases which not only include the project data, but also metadata such as authors, papers, citations, figures, tables, etc.  
it is known as "scholarly" due to its main use by academics

By combining information on scholarly data, we are able to form what is called a scholarly network, which can be a network of authors, journals, institutions, etc. that are connected together through collaborative works and relationships
By understanding this, we can learn about things outside of the projects such as how researchers interact with each other, find relationships between researchers hidden in citation networks, observe impact of funding in an institution, or allocate resources to different departments.
but for the purposes of this project, our goal is simply to explore our own scholarly network by looking at extra authors or journals that could be helpful for research topics
	

For our model, we will use the NCBI, or the National Center for Biotechnology Information as our data source.  This is a vast online resource containing an innumerable amount of documents, relating to biology and medicine

When it comes to data extraction however, we will want to use Entrez which is NCBI's primary text search and retrieval system.  This has a very convenient python package that lets us pull scholarly data from the NCBI servers directly to our notebooks

Putting it all together, our code submits a keyword using the entrez python package, and in the case of this project, we will be using the term 'hay fever'; entrez will search ncbi for any documents relating to hay fever and return anything that it can fine for us to input into our dataframes; 

to begin we can do some simple exploratory data analysis; here we can view the authors that contributed the most amount of publications to our search term

next we can look at the number of publications in the past century; as seen , the number of submitted publications peaked at around 2010 but has slowly gone down ever since; this could be due to lack of interest after enough research has been done or just that the collection of documents is incomplete

when it comes to data preprocessing, luckily since all the data is professionally inputted, the large majority of them are already very neat and do not need much major cleaning.
Something we can do however is to drop some metadata columns that we do not need; while metadata such as authors and abstract are important, we don't need every detail such as publication page number or list of investigators

to actually choose significant documents, we want documents that are high quality enough to have made an impact on the academic community; a good metric for determining this is by how many times a document has been referenced or cited by others, as a document that has been widely used is sure to be significant

though an issue we found is that not all documents have reference numbers; this could simply be because that the document hasn't been exposed to certain communities yet; since we don't want to disregard the fact that an unknown student in the middle of nowhere could still write an amazing paper, we can use NLP with a logistic regression model and have its significance as its target variable; in here we want to focus on precision, as we want to make sure the documents the model classifiers are actually true positive

after using our model to predict significance of unknown documents, we can merge them back with the other data and choose the document with the most reference numbers our of the documents that we considered significant; in this case we have the document Allergic Rhinitis and its Impact on Asthma

next we can take our best document and then discover similar ones using cosine similarity in a content-based recommendation system

in the end we have some explanatory data analysis; explanatory data is different compared to exploratory as exploratory is more for initial data visualization while explanatory is more for visualizing the results

one such way is through an author collaboration plot; in here, we have the top 30 authors plotted in a circle, with a line connecting them to any author that they have a connection with.  A connection is denoted by anytime two or more authors have worked together, or used each others work in citations, and a thicker line symbolizes more collaborations.  We can take the author of our recommended papers, and find thick lines from him or her to find similar authors that we can also look at

next would be to look at sunplots, here we have the journals that have published our recommended articles, and contains the top five authors under them based on number of articles published



and then here are the contacts, thank you 
