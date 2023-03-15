# Personalized AI chatbot using ChatGPT using your own data set.

This project shows how to use the OpenAI API and LlamaIndex to create a personalized chatbot that can process your own text documents to generate curated responses. Although it is posible to use other LLMs (Large Language Models), like the free alternative LangChain, for this example we are using the commercial license of ChatGPT. That's why the code provided in this GitHub will not be functional without a your personal API key from OpenAI.

By Luis David Preciado, UNAL

## Sources
[OpenAI API](https://openai.com/blog/openai-api)

[LlamaIndex](https://gpt-index.readthedocs.io/en/latest/index.html)

[Quick Introductory Guide](https://bootcamp.uxdesign.cc/a-step-by-step-guide-to-building-a-chatbot-based-on-your-own-documents-with-gpt-2d550534eea5)

## Python Code
### Libraries
First we need to install the necessary Python libraries. To do this run the following lines in your console:
```
pip install llama-index
pip install openai
pip install PyPDF2
```
LlamaIndex is what we will be using to generate the data structures that can be read by ChatGPT. The OpenAI library will help us connect to the API and validate our key. Also it will keep track of the spent tokens for the billing. Finally, PyPDF will allow us to read PDF files.

### Setting up the chatbot
We will be using a Jupyter Notebook as a developing environment, especially for the ability to run code blocks. So we don't index all our documents everytime we run the chatbot. This will help us save money in tokens.

In the notebook we need to import the libraries we just installed:
```
# Import necessary packages
from llama_index import GPTSimpleVectorIndex, Document, SimpleDirectoryReader
import os
```
And then connect with the OpenAI API:
```
os.environ['OPENAI_API_KEY'] = '<key>'
```
We will no be providing a key because it is a paid service.

Next we will load our data that will be saved in this case in a folder called "data" in the same directory.
```
# Loading from a directory
documents = SimpleDirectoryReader('data').load_data()
```
If you want to save the index and load it for future use, you can use the following methods:
```
# Save your index to a index.json file
index.save_to_disk('index.json')
# Load the index from your saved index.json file
index = GPTSimpleVectorIndex.load_from_disk('index.json')
```
Finally we can ask a question or query to ChatGPT and it can will be responded based in the documents inside our index.
```
# Querying the index
response = index.query("<query>")
print(response)
```
A notebook file and some source data will be loaded in this Git so you can test it yourself.

## Final Thoughts
This is an introduction to creating a personalized chatbot using the most powerfull LLM at the moment that can retrieve, summarize and analize informations in your personal documents.

This is a very powerful tool, especially in the industrial application of AI. Because we can save time teaching the AI the processes and information of our company and jump straight to the generation of information. The AI is capable of cross refering your personal data set with its own to expland and analyze the information.

This is just the tip of the iceberg of the tools and implementations of this technology. Other functionalities not touched in this document include: creating a tree of indexed data to give a hierarchy to the sources; accessing information from Google Drive, Notion, Discord and even structured data like SQL; refining the prompts using keywords and many others.
