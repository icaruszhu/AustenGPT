
# AustenGPT


This project repurpose the small but versatile
[NanoGPT](https://github.com/karpathy/nanoGPT) for training Jane Austen’s published works in the early 19th century. 


![austen-word-cloud](assets/austen-cloud-250-word.png)

# Pre-processing: Code for getting and cleaning up Austen’s works for training 
```sh

```

**  

[config/train_austen_char.py](config/train_austen_char.py) config file:

```sh
python train.py config/train_austen_char.py
```

```sh
python sample.py --out_dir=out-austen-char
```

This generates a few samples, for example:

```

```



```sh
python train.py config/train_shakespeare_char.py --device=cpu --compile=False --eval_iters=20 --log_interval=1 --block_size=64 --batch_size=12 --n_layer=4 --n_head=4 --n_embd=128 --max_iters=2000 --lr_decay_iters=2000 --dropout=0.0
```

