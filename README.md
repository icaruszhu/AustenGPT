
# NB: This repo is a work in progress. Code and explantary text is being added gradually. 


# AustenGPT
 
This project repurposes the small but versatile
[NanoGPT](https://github.com/karpathy/nanoGPT) for training Jane Austen’s published works in the early 19th century. It is made to accompany the fortcoming paper “AustenGPT: Organic Composition and AI Creation with Jane Austen's Novels”. 

The repo hosts the code showing steps for building the two Austen corpuses, one for basic exploratory quantitative text analysis and other for AI traning. Here are the two corpuses specifically built for this project.

- `/data/austen_qta/austen_ qta.csv`
- `/data/austen-char/austen-sans-quotes.txt`

We have tried our best to show how we achieve our results to allow fellow researcher to experiment with the corpuses, replicate and critique research findings. More details will be available from the above paper.

## Exploratory QTA  
### The Austen Word Cloud (max 250 words)
![austen-word-cloud](assets/austen-cloud-250-word.png)
### Keyness plotting of Pride and Prejudice (target) against the whole Austen corpus as reference using R
![P&P keyness](assets/pride_keyness_plot.png)

# AI Training (with `austen-sans-quotes.txt`)
- The AI training takes three steps with three commands

## 1) Prepare 
- The first step tokenises the Austen corpus and it splits the corpus into 90% for traning and 10% for validation to avoid overfitting. We can the below command with the customised `prepare-austen-char.py`. Simply run this:

```sh
python data/austen_char/prepare-austen-char.py        

```
The result would show there are 81 unique characters as the vocabulary size. The train dataset has 3,636,652 tokens, while the validation set has 404,073 tokens.


## 2) Train

We need to make a customised configure file  [train_austen_char.py](config/train_austen_char.py) for training the `austen_char` corpus. Then run this command:

```sh
python train.py config/train_austen_char.py
```


## 3) Sample: generate some text
Finally, generate some text by using the `sample.py` command. Note that we need to specify the output directory `out_dir` as `out-austen-char`

```sh
python sample.py --out_dir=out-austen-char
```
We can also give a prompt word (e.g. “handsome”) like this:
```sh
python sample.py --out_dir=out-austen-char --start="handsome"
```

Generated text would look like this (Depending how many iterations that the training has gone through, the quality of text can vary):

```

```

# Repurposing and resusing AustenGPT
AustenGPT can be repurposed thanks to NanoGPT’s versatile architecture! It can be modified to train other corpuses even including non-English texts. For example, this repo includes a corpus of Li Qingzhao (李清照 or 李易安)’s 49 poems for experimentation. [Li (1084 - 1155)](https://en.wikipedia.org/wiki/Li_Qingzhao) is one of the greatest Chinese female poets active in the Song Dynasty. The prepared corpus is in ~data/yian-char~ and its config file is ~config/train-yian-char~. Simply apply the three steps with slightly modified code.

```{python}
python data/yian_char/prepare-yian.py
```
This will tokenise the ~yian-char~ corpus which contains 960 characters. It is split into two sets, with the training set containing  4,566 tokens and the valuation set 508 tokens.

Then train the ~yihan-char~ corpus:

```{python}
python train.py config/train_yian_char.py --device=cpu --compile=False --eval_iters=20 --log_interval=1 --block_size=64 --batch_size=12 --n_layer=4 --n_head=4 --n_embd=128 --max_iters=5000 --lr_decay_iters=500 --dropout=0.0

```
Finally sample it to generate some text similar to Li Qingzhao’s poetry.

```{python}
python sample.py --out_dir=out-yian-char --device=cpu
```




