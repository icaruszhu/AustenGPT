
# NB: This repo is a work in progress. Code and explantary text is being added gradually. 


# AustenGPT
 
This project repurposes the small but versatile
[NanoGPT](https://github.com/karpathy/nanoGPT) for training Jane Austen’s published works in the early 19th century. It is made to accompany the fortcoming paper “AustenGPT: Organic Composition and AI Creation with Jane Austen's Novels”. 

The repo hosts the code showing steps for building the two Austen corpuses, one for basic exploratory quantitative text analysis and other for AI traning. Here are the two corpuses specifically built for this project.

- ~/data/austen_qta/austen_ qta.csv~ 
- ~/data/austen-char/austen-sans-quotes.txt~ 

We have tried our best to show how we achieve our results to allow fellow researcher to experiment with the corpuses, replicate and critique research findings. More details will be available from the above paper.

## Exploratory QTA  
### The Austen Word Cloud (max 250 words)
![austen-word-cloud](assets/austen-cloud-250-word.png)
### Keyness plotting of Pride and Prejudice (target) against the whole Austen corpus as reference using R
−![P&P keyness](assets/pride_keyness_plot.png)

# AI Training (with ~austen-sans-quotes.txt~)

## Pre-processing: Code for getting and cleaning up Austen’s works for training [to be added]
```sh
python data/austen_char/prepare-austen-char.py        

```
The result shows there are 81 unique characters as the vocabulary size. The train dataset has 3,636,652 tokens, while the validate set has 404,073 tokens.


## Configure `train_austen_char.py` for training the `austen_char` corpus [to be completed]

[config/train_austen_char.py](config/train_austen_char.py) config file:

## Prepare: Tokenise the corpus
- Split the corpus into 90% for traning and 10% for validation to avoid overfitting.
```{sh}


```


## Train
```sh
python train.py config/train_austen_char.py
```

python sample.py --out_dir=out-austen-char
```

Generated texts look like this:

```



## Sample: generate some text
```sh
python sample.py --out_dir=out-austen-char
```

Generated texts look like this:

```

```



