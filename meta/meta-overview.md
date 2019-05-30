* forward_index es usado para aplicaciones tales como 'modelado de tópicos', 'clasificación'.
* inverted_index es usado para crear motores de búsqueda, clasificación con KNN

# formato de entrada de corpus

en un archivo de configuración .toml, hay 2 parametos para especificar un corpus:

    dataset = "dataset-name"
    corpus = "name.toml"

'dataset' es un folder donde el corpus reside.
'corpus' es el path al archivo de configuración del corpus. ej: corpus por linea ('corpus' = 'line.toml')

4 formatos de corpus:

1. corpus por linea (line):

A line_corpus consists of one or two files:

line.toml: the corpus configuration file
corpusname.dat: each document appears on one line.
corpusname.dat.labels: optional file that includes the class or label of the document on each line, again corresponding to the order in corpusname.dat. These are the labels that are used for the classification tasks.

2. file corpus:

In a file_corpus, each document is its own file. Your corpus configuration file (typically file.toml) should specify a list key to point MeTA at a list of all of the documents in your corpus. This file, list-full-corpus.txt (where list is whatever you set the list key to in your configuration file; typically just the name of the corpus again) contains (on each line) a required label for each document followed by the path to the file on disk (separated by a tab or a space). If the documents don’t have specified class labels, just precede the line with [none] or similar.

For example, your file.toml might look like:

type = "file-corpus"
list = "dataset"
encoding = "utf-8" # optional; this is the default
num-docs = 1000    # optional
metadata = [{name = "path", type = "string"}]    # metadata explained later
and the file dataset-full-corpus.txt might look like:

class-label	relative/path/to/document01.txt
class-label2	relative/path/to/document02.txt
class-label	relative/path/to/document03.txt
class-label3	relative/path/to/document04.txt