# GraphWSD (TextGraphs-16 COLING 2022)

Official code repository: **Word Sense Disambiguation of French Lexicographical Examples Using Lexical Networks** 

[[Paper](https://aclanthology.org/2022.textgraphs-1.8/)]  [[PPT](https://docs.google.com/presentation/d/1uU2jxzjJwMPJA9z1oH65imlzaKltZfinsFFlHlp3RBo/edit?usp=sharing)]

## Folder Description

`/data/` : contains instructions to organize the `data/` folder

`/scripts/` : contains individual script modules


## Steps to run the experiments:

1) Clone the repo : `git clone https://github.com/ATILF-UMR7118/GraphWSD.git`

2) Create the virtualenv

```
python3 -m venv wsdvenv
. wsdvenv/bin/activate
pip3 install --upgrade pip
cd GraphWSD/
pip3 install -r requirements.txt
```

3) Follow the instructions provided in `data/` folder

4) To run the models for NOUN/VERB wsd:

(a.1) STRUCT model

```
python3  ~/GraphWSD/scripts/wsd_ewiser.py \
        --data ~/GraphWSD/data/ortolang/nountmp/ \
        --save_dir ~/GraphWSD/scripts/ortolog/ \
        --num 100  --model_num onoun_ewiser_29061156 --mtype ewiser --save-model \
        --learning 0.001  --hidden 8000 --batch 64 --device cuda --embed 768 --lm camembert-base
```
(a.2) STRUCT* model

```
python3  ~/GraphWSD/scripts/wsd_ewiser.py \
        --data ~/GraphWSD/data/ortolang/nountmp/ \
        --save_dir ~/GraphWSD/scripts/ortolog/ \
        --num 100  --model_num onoun_ewiser_29061156 --mtype ewiser --save-model \
        --learning 0.001  --hidden 8000 --batch 64 --device cuda --embed 768 --lm camembert-base --trainable
```
(a.3) STRUCT** model

```
python3  ~/GraphWSD/scripts/wsd_ewiser.py \
        --data ~/GraphWSD/data/ortolang/nountmp/ \
        --save_dir ~/GraphWSD/scripts/ortolog/ \
        --num 100  --model_num onoun_ewiser_29061156 --mtype ewiser --save-model \
        --learning 0.001  --hidden 8000 --batch 64 --device cuda --embed 768 --lm camembert-base --fragment --trainable
```
(b.1) SEM model

```
python3  ~/GraphWSD/scripts/wsd_ewiser.py \
        --data ~/GraphWSD/data/ortolang/nountmp/ --num 100 \
        --save_dir ~/GraphWSD/scripts/ortolog/  --model_num onoun_seml_29061522 \
        --mtype ewiserc --save-model --batch 64  --device cuda --semantics\
          --hidden-dim 8000  --embed 768 --lm camembert-base 
```
(b.2) SEM* model

```
python3  ~/GraphWSD/scripts/wsd_ewiser.py \
        --data ~/GraphWSD/data/ortolang/nountmp/ --num 100 \
        --save_dir ~/GraphWSD/scripts/ortolog/  --model_num onoun_seml_29061522 \
        --mtype ewiserc --save-model --batch 64  --device cuda --semantics\
          --hidden-dim 8000  --embed 768 --lm camembert-base --trainable
```
(b.3) SEM** model

```
python3  ~/GraphWSD/scripts/wsd_ewiser.py \
        --data ~/GraphWSD/data/ortolang/nountmp/ --num 100 \
        --save_dir ~/GraphWSD/scripts/ortolog/  --model_num onoun_seml_29061522 \
        --mtype ewiserc --save-model --batch 64  --device cuda --semantics\
          --hidden-dim 8000  --embed 768 --lm camembert-base --fragment --trainable
```

## Different configurations 

STRUCT and SEM are two strategies to intialize $A$ adjacency matrix. Any $a_{i,j} \in A$ is $\sum w(r)$ where $r \in S_{i,j}$ and $S_{i,j}$ is set of edges between i and j nodes.

STRUCT : count number of edges

SEM : count weight (strength) of  edges. SEM model requires `--semantics`

|config|interpretation|command|
|---|---|---|
|STRUCT/SEM| A is frozen ||
|STRUCT/SEM *| $a_{i,j}$ is trainable | --trainable |
|STRUCT/SEM **| $w(r)$ is trainable | --trainable --fragment |


For any questions related to repository contact: `asinha@atilf.fr`

## Citation

```bibtex
@inproceedings{sinha2022word,
  title={Word sense disambiguation of french lexicographical examples using lexical networks},
  author={Sinha, Aman and Ollinger, Sandrine and Constant, Mathieu},
  booktitle={TextGraphs-16: Graph-based Methods for Natural Language Processing},
  pages={70--76},
  year={2022}
}

```
