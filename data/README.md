# Instruction to organize the data to run the models

## Folder Description

* The `data/` folder contains a version of ORTOLANG  folder `verion_31iii21/` used for the experiments. It contains 2 folders: `BEL-RL-fr/` and `RL-fr/`.

* The subdirectory `BEL-RL-fr/` contains AllSources_{nouns/verbs}.xml files.
* The subdirectory `RL-fr/` contains 3 utility files : `01-lsnodes.csv`, `02-lsentries.csv` and `15-lslf-rel_boost.csv`

## To run experiment with preprocessed files
Use directly the files in `preprocessed_data/` folder which contains two zip folder `nountmp.zip` and `verbtmp.zip`. Unzpip the two folder, that you are ready to run the main scripts!



## Preprocessing Pipeline for creating the files in `preprocessed_data/`

```
mkdir preprocessed_data

python scripts/utils.py --name ortolang --version 1 		
						--save_dir ./data/preprocessed_data/ 
						--home ~/GraphWSD/ 
						--xml ~/GraphWSD/data/version_31iii21/BEL-RL-fr/V2-ORTOLANG/XML-POS/ --write --keep  
						--pos noun
```

In case of any question, write to this email ```aman.sinha@atilf.fr```
