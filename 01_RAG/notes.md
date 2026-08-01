## Retrival Augmented Generation

**Definition** - Process of optimizing O/P of LLM, so it references an authoritative knowledge based outside its training data sources before generating a response.


**Disadvantages of LLM** - 1.Hallucination  2. Knowledge Gap

to solve this problem, we have RAG 

in RAG we will have external vector database in which there is data ingestion pipeline


## Pipeline of RAG

Pipeline 1 - Data Ingestion Pipeline

**DATA ---> PARSING ----> Embedding -----> stored in vector database**

DATA ------> can be in SQL,PDF,Excel

PARSING -----> How do you read the data and chunk the data

Embedding ------> convert numbers to vectors so that algo like similarity search
                    will be applied to every chunk

Embedding has models ---> google embedding, Hugging face embedding


So Vector DB is basically knowledge base which is offline for the company only

#### This is known as Data Ingestion Pipline


**Document Structure**

Data Parsing ---> Document structure

Now we convert entire data into Chunks

_Q.Why we need chunks?_

We divide document into smaller parts because any LLM can have some limit of context size
so to manage the context size and perform embedding(converting text to vectors) we do chunking
of the files.


Pipeline 2 - 

Now query will go to embedding bring some context and Prompt that we have already
given and generate the answer

#### This is known as Query Retrival Pipline




## Part 2 - Practical Hands on

step 1 - uv init

step 2 - uv venv

step 3 - activate vitualenv

step 4 - create requirements.txt

<!-- langchain_community==0.0.75
langchain_core==0.0.49
langchain==0.2.10
ipykernel
pypdf 
pymupdf -->

step 5 - install them using uv add -r requirements.txt

step 6 - Create data and notebook folder



### HOw to load documents of any extension

step 1 - import Document from langchain_core.document

step 2 - import the document loader you need from langchain_community.document_loaders 

step 3 - structre 

example : -


    dir_loader = DirectoryLoader(
    "../data/PDF",
    glob = "**/*.pdf",
    loader_cls = PyMuPDFLoader,
    show_progress = False
)

example 2- 

loader = DirectoryLoader(
    "../data/text_files",
    glob = "**/*.txt",
    loader_cls=TextLoader,
    loader_kwargs={"encoding":"utf8"},
    show_progress = False
)



### How to do chunking