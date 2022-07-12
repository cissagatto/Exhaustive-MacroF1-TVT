# Exhaustive MacroF1

This code is part of my doctoral research at PPG-CC/DC/UFSCar. The aim is built, validate and test random partitions for multilabel classification. Important, this code will execute on Windows and Linux.

The *exhaustive partitions* experiment differs from *oracle partitions*. In the *oracle* experiment, all partitions generated by the bell number are directly tested in the CLUS framework. Then, the partition with the best macro-F1 is chosen. In the *exhaustive* experiment, each partition generated by the bell number is first validated. Then, the partition with the best macro-F1 is chosen to be tested.

The figure shows an example with a dataset that generates 4140 partitions and is executed in 10-folds cross-validation.

<img src="https://github.com/cissagatto/Exhaustive-MacroF1-TVT/blob/main/images/exhaustive-clus.png" width="500">

## How to cite 
@misc{Gatto2021, author = {Gatto, E. C.}, title = {Exhaustive Partition Experiment with Macro-F1}, year = {2021}, publisher = {GitHub}, journal = {GitHub repository}, howpublished = {\url{https://github.com/cissagatto/Exhaustive-MacroF1-TVT}}}

## IMPORTANT!! PLEASE READ BEFORE RUNNING

All of my experiments use the validation, train and set test. But, in this version, the code uses only the train and test sets and the validation set is ignored. This code was implemented thinking of that situation. Please, pay attention to this. You need to generated these sets when runing the multi-label cross-validation code.

## Types of Exhaustive Partitions
<img src="https://github.com/cissagatto/Exhaustive-MacroF1-TVT/blob/main/images/tipos_particoes_exhaustiva.png" width="500">

## Scripts
This source code consists of an R project for R Studio and the following R scripts:

1. libraries
2. utils
3. validation
4. test
5. exhaustive

## Bell Partitions
<img src="https://github.com/cissagatto/Exhaustive-MacroF1-TVT/blob/main/images/Bell-Partitions.png" width="300">

## FlowChart
<img src="https://github.com/cissagatto/Exhaustive-MacroF1-TVT/blob/main/images/Exhaustive-Horizontal.png" width="300">

## Folder Structure
<img src="https://github.com/cissagatto/Exhaustive-MacroF1-TVT/blob/main/images/estrutura.png" width="300">

## Preparing your experiment

### Step-1
This code is executed in X-fold cross-validation. First, you have to obtain the X-fold cross-validation files using this code: https://github.com/cissagatto/CrossValidationMultiLabel (all the instructions to use the code are in the Github). After that, put the results generated in the *datasets* folder in this project. The folder structure generated by the code CrossValidation is used here.

### Step-2
After obtained the X-Fold Cross-Validation and put in the correct folder, you need the Bell Partitions. The code to generated the Bell Partitions is available here https://github.com/cissagatto/BellPartitionsMultiLabel. Please, follow the instructions in GitHub. After generated the bell partitions, put them in the *BellPartitions* folder. The folder structure is maintained.

### Step-3
Confirms if the folder *utils* contains the following files: *Clus.jar*, *R_csv_2_arff.jar*, and *weka.jar*, and also the folder *lib* with *commons-math-1.0.jar*, *jgap.jar*, weka.jar and *Clus.jar.* Without these jars, the code not runs. 

### Step-4
Place a copy of this code in _C:/Users/[username]/Exhaustive-MacroF1-TVT_ or _/home/[username]/Exhaustive-MacroF1-TVT_. Our files are configured to obtain the paths of the folders from this path. You can change this in the code if you want.

### Step-5
A file called _datasets.csv_ must be in the *datasets* folder. This file is used to read information about the datasets and they are used in the code. All 74 datasets available in Cometa are in this file. If you want to use another dataset, please, add the following information about the dataset in the file:

_Id, Name, Domain, Labels, Instances, Attributes, Inputs, Labelsets, Single, Max freq, Card, Dens, MeanIR, Scumble, TCS, AttStart, AttEnd, LabelStart, LabelEnd_

The _Id_ of the dataset is a mandatory parameter (_n_dataset_) in the command line to run all code. The fields _LabelStart_ and _LabelEnd_ are used in a lot of internal functions. Please, make sure that this information is available before running the code.

## Software Requirements
This code was develop in RStudio Version 1.2.5001 © 2009-2019 RStudio for Linux, Inc.Build 93 (7b3fe265, 2019-09-18) Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) QtWebEngine/5.12.1 Chrome/69.0.3497.128 Safari/537.36. The R language version was R version 4.0.5 (2021-03-31) with x86_64-pc-linux-gnu (64-bit). Please make sure all the dependencies are installed (verify libraries.R). This code does not provide an installation of R packages.

## Hardware Requirements
This code may or may not be executed in parallel, however, it is highly recommended that you run it in parallel. The number of cores can be configured via the command line (_number_cores_). If *number_cores = 1* the code will run sequentially. In our experiments, we used 10 cores. For reproducibility, we recommend that you also use 10 cores.

Important: we used the CLUS classifier in this experiment. This implies generating all physical ARFF training and testing files for each of the generated partitions. Our code generates the partitions first in memory and then saves them into the HD. However, to avoid memory problems, immediately after saving to HD, the files are tested and then deleted. Even so, make sure you have enough space on your HD and enough available RAM for this procedure.

# Run

```
Rscript exhaustive.R [number_dataset] [number_cores] [number_folds]
```

_number_dataset_: dataset number according to file "datasets.csv" in the folder root

_number_cores_: cores to parallel

_number_folds_: number of folds to cross-validation


Example:

```
Rscript exhaustive.R 24 10 10
```

This will compute all partitions for dataset *Flags*, using 10 cores and 10-folds for cross-validation. If you want, you can modify the file *exhaustive.R* to execute only for one partition. You also can modify the code to upload the results into your google drive using *rclone*. 


## Acknowledgment
This study is financed in part by the Coordenação de Aperfeiçoamento de Pessoal de Nível Superior - Brasil (CAPES) - Finance Code 001

## Links

[Post-Graduate Program in Computer Science](http://ppgcc.dc.ufscar.br/pt-br)

[Computer Department at UFSCar](https://site.dc.ufscar.br/)

[Biomal](http://www.biomal.ufscar.br/)

[CAPES](https://www.gov.br/capes/pt-br)

[Embarcados](https://www.embarcados.com.br/author/cissa/)

[Linkedin](https://www.linkedin.com/in/elainececiliagatto/)

[Linkedin](https://www.linkedin.com/company/27241216)

[Instagram](https://www.instagram.com/cissagatto)

[Facebook](https://www.facebook.com/cissagatto)

[Twitter](https://twitter.com/cissagatto)

[Twitch](https://www.twitch.tv/cissagatto)


## Report Error

Please contact me: elainececiliagatto@gmail.com

# Thanks
