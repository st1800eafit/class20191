# compilación de meta en ubuntu 16.04:

link: https://meta-toolkit.org/setup-guide.html

## clone the project
    mkdir $HOME/bin
    cd $HOME/bin
    git clone https://github.com/meta-toolkit/meta.git
    cd meta/

## set up submodules
    git submodule update --init --recursive

## set up a build directory
    mkdir build
    cd build
    cp ../config.toml .

## configure and build the project
    cmake ../ -DCMAKE_BUILD_TYPE=Release
    make
    
## You can now test the system by running the following command:

    ./unit-test --reporter=spec

# Tutorial básico:

link: https://meta-toolkit.org/profile-tutorial.html

## doc.txt from: The Project Gutenberg EBook of Metamorphosis, by Franz Kafka

    cd $HOME/bin/meta/build
    wget http://www.gutenberg.org/cache/epub/5200/pg5200.txt -O doc.txt

## Stop word removal

Remove the stop words from your document by running the following command:

    cd $HOME/bin/meta/build

    ./profile config.toml doc.txt --stop

The output should be saved to the file doc.stops.txt. 

## Stemming

{run, runs, running} -> run
{argue, argued, argues, arguing} -> argu
{lies, lying, lie} -> lie
Reduce all words down to their stems in your document by running the following command:

    ./profile config.toml doc.txt --stem

The output should be saved to the file doc.stems.txt. 

## Frequency analysis

### a bag of individual words

    ./profile config.toml doc.txt --freq-unigram

# a bag of two consecutive word sequences

    ./profile config.toml doc.txt --freq-bigram

# a bag of three consecutive word sequences
    ./profile config.toml doc.txt --freq-trigram

## Natural language processing (NLP)

### Part-of-speech tagging

Ensure that you have a section in config.toml that looks like the following:

[sequence]
prefix = "path/to/your/tagger/folder/"
Now, you should be able to POS-tag your doc.txt by running the following command:

    ./profile config.toml doc.txt --pos

The output should be written to doc.pos-tagged.txt. 

### Parsing

links: https://github.com/meta-toolkit/meta/releases

    download: 

    cd $HOME/bin/meta/build
    wget https://github.com/meta-toolkit/meta/releases/download/v3.0.2/greedy-perceptron-tagger.tar.gz
    gunzip greedy-perceptron-tagger.tar.gz
    tar xvf greedy-perceptron-tagger.tar

Ensure that you have a section in config.toml that looks like the following:

[parser]
prefix = "path/to/your/parser/folder/"
Since the parser relies on having POS-tagged sentences, ensure that you’ve done the part-of-speech tagging section of this tutorial as well.

Parse the sentences in doc.txt by running the following command:

    ./profile config.toml doc.txt --parse

The output should be written to doc.parsed.txt.