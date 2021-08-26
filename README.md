# Legal-NLP-Project

Developed a system for US BVA (Board of Veteran's Appeals) decisions, which can be used to automate sentence annotations on BVA decisions.

## Dataset

99 BVA decisions with annotations, including 33 granted, 33 denied, and 33 amended decisions. The annotation with a type system has been inspired by existing work on BVA opinions. 

101k BVA decisions without annotations, which used for development of word embeddings.





# Legal-NLP-Project

Developed a system for US BVA (Board of Veteran's Appeals) decisions, which can be used to automate sentence annotations on BVA decisions.

## Dependencies

* Python 3
* Spacy
* Fasttext
* LUIMA SBD (https://github.com/jsavelka/luima_sbd.git)

## Usage

The system provides two functions, setup() and analyze(str) => [(str, str)].

First, call the setup() function, which set up all needed dependencies.

Then call analyze(str) function which takes a single text string as an input, applies the best model, and returns a list of split sentences along with the name of types they have been classified as. 

## Dataset

- Labeled corpus of 99 BVA decisions with annotations, including 33 granted, 33 denied, and 33 amended decisions. The annotation with a type system has been inspired by existing work on BVA opinions. 

- Unlabeled corpus of 101k BVA decisions without annotations, which used for development of word embeddings.

  

## Procedures

- Deciding on a Sentence Segmenter

  Compared several sentence segmenters and analyze their performance on BVA decisions.

- Preprocessing

  Sentence-segment all decisions in the unlabeled corpus and split sentence into tokens using tokenizer. 

- Developing Word Embeddings

  Trained a word embedding model on the compiled, tokenized, unlabeled data.

- Featurization

  - Produced a TFIDF featurization of training, dev, and test data.
  - Produced a Word Embedding featurization based on the embedding model built on the unlabeled corpus.

- Training Classifiers 

  Based on two different featurizations, trained the following models:

  - Logistic Regression Model
  - Random Forests Model

- Error Analysis

  The best model is Random Forests Model based on Word Embedding Featurization, which reached the macro average F1 score of 0.65.
