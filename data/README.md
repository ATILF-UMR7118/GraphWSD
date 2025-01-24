# Instruction to organize the data to run the models

## Folder Description

* The `data/` folder contains a version of ORTOLANG folder `version_31iii21/` used for the experiments. It contains 2 folders: `BEL-RL-fr/` [version2, ref. 1] and `RL-fr/` [version2.1 , ref. 2].

* The subdirectory `BEL-RL-fr/` contains AllSources_{nouns/verbs}.xml files.
* The subdirectory `RL-fr/` contains 3 utility files : `01-lsnodes.csv`, `02-lsentries.csv` and `15-lslf-rel_boost.csv`

## To run experiment with preprocessed files
Use directly the files in `preprocessed_data/` folder which contains two zip folder `nountmp.zip` and `verbtmp.zip`. Unzip the two folder, that you are ready to run the main scripts!



## Preprocessing Pipeline for creating the files in `preprocessed_data/`

```
mkdir preprocessed_data

python scripts/utils.py --name ortolang --version 1 		
						--save_dir ./data/preprocessed_data/ 
						--home ~/GraphWSD/ 
						--xml ~/GraphWSD/data/version_31iii21/BEL-RL-fr/V2-ORTOLANG/XML-POS/ --write --keep  
						--pos noun
```


## References

[1] Analyse et traitement informatique de la langue française - UMR 7118 (ATILF) (2024). BEL-RL-fr [Corpus]. ORTOLANG (Open Resources and TOols for LANGuage) - www.ortolang.fr, v2, https://hdl.handle.net/11403/examples-ls-fr/v3.1.

[2] Analyse et traitement informatique de la langue française - UMR 7118 (ATILF) (2021). Réseau Lexical du Français (RL-fr) [Lexique]. ORTOLANG (Open Resources and TOols for LANGuage) - www.ortolang.fr, v2.1, https://hdl.handle.net/11403/lexical-system-fr/v2.1.


## Questions?

In case of any questions, write to this email ```aman.sinha@atilf.fr```