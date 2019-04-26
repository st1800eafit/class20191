# 1. Task 1: Stopword Removal
    ./analyze ../config.toml Assignment1/doc.txt --stop

# 2. Task 2: Stemming

# 3. Task 3: Part-of-Speech Tagging

# 4. Build the Search Engine

## 4.1 Exploring the Dataset

    cd $HOME/bin/Assignment_1
    cp -rp moocs/moocs.dat.zip ../meta/data/moocs/
    cp -rp moocs/metadata.dat.zip ../meta/data/moocs/

    cd $HOME/bin/meta/data/moocs/
    unzip moocs.dat.zip
    unzip metadata.dat.zip

The MOOCs dataset contains the descriptions found on the webpages of around 23,000 MOOCs (Massive Open Online Courses). You will start by exploring the dataset. Navigate to Assignment_1/moocs. This directory contains the files that describe the dataset.

moocs.dat contains the content of the webpages of all the MOOCs; each MOOC's main page occupies exactly one line in the file. Feel free to open the file to get an idea about the contents, but be wary that it is a large file and might take some time to load.

metadata.dat contains the names and the URLs of the MOOCs. The entry on line x in metadata.dat corresponds to the MOOC on line x in moocs.dat.

moocs-queries.txt contains a set of queries that you will use to evaluate the effectiveness of your search engine.

moocs-qrels.txt contains the relevance judgments corresponding to the queries in moocs-queries.txt. Each line in moocs-qrels.txt has the following format: (querynum documentID 1). This means that the document represented by documentID is a relevant document for the query whose number is querynum. The relevance judgments in moocs-qrels.txt were created by human assessors who ran the queries and chose the relevant documents. Later on in the assignment, you are going to use these judgments to quantify the performance of your search engine.

## 4.2 Indexing MOOCS

To index the dataset, in the Assignment_1/build directory run:

    cd Assignment_1/build
    ../../meta/build/index ../config.toml

## 4.3 Searching

    cd Assignment_1/build
    ../../meta/build/interactive-search ../config.toml

## 4.4 BM25

Evaluate the performance of bm25 with default parameters (i.e., do not change config.toml) by running:

    cd Assignment_1/build
    ./ranking-experiment ../config.toml task4

## 4.5 BM25 with tuned parameters

Change the parameter b of bm25 in config.toml to 0.75

    [ranker] 
    method = "bm25" 
    k1 = 1.2 
    b = 0.75 
    k3 = 500

and run again:

    cd Assignment_1/build
    ./ranking-experiment ../config.toml task5

# 4.6 Relevance Judgments

    cd Assignment_1/build
    ./relevance-judgements ../config.toml