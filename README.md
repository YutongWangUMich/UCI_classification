# UCI_classification

UCI classification datasets loading utilities.

## Run this first

You need to be in the same directory as the `setup.sh` file. Run the following in shell.

```
chmod +x setup.sh
./setup.sh
```

*What does the above do?*

1. Downloads `data_py.zip` (39 MB) from 'http://www.bioinf.jku.at/people/klambauer/data_py.zip'. This link is listed at the Self-Normalizing Network repository https://github.com/bioinf-jku/SNNs.
2. Unzips `data_py.zip` to `data/` (268M when unzipped).
3. Cleans up the naming conventions of the subdirectories of `data/` and deletes an unused file (`data/abalone_dat.py`) in the directory.
4. Make a copy of `_datasets.py` to `datasets.py` and append the full directory path to the file, so that the data files can be found.

## How to use this

See `jupyter_notebooks/02_LR_TF_example.ipynb` for a logistic regression example implemented in TensorFlow.


## Files and directories


### Raw data files

`data/` - contains the raw data files (feature vectors, labels, validation sets)

The format is the same as in the original compilation in https://github.com/bioinf-jku/SNNs and is shown below:

```
data/
├── DATASETNAME/
│   ├── DATASETNAME_py.dat           # feature vectors
│   ├── folds_py.dat                 # the train and test split
│   ├── labels_py.dat                # labels (0,1,...,num_classes)
│   └── validation_folds_py.dat      # 4-fold splits of the training set
└── ...
```

where `DATASETNAME` stands for `abalone`, `iris`, etc.

### Curated lists of datasets

Lists of datasets

```
data_list/
├── all.txt                          # the list all datasets
├── arora2019harnessing.txt          # list of 90 datasets considered in [Arora et al, 2019]
└── testing.txt                      # three datasets: [iris, ionosphere, wine]. Useful for testing.
```

[Arora et al, 2019](https://arxiv.org/abs/1910.01663)


### Metadata about the datasets `metadata/`

```
metadata/
├── datasets_summary.csv              # a table of summary of essential informations of each dataset
└── L2_dist_est.csv                   # precomputed values of L2_dist_est, see code chunk below and [Shankar et al 2020].
```    

[Shankar et al 2020](http://proceedings.mlr.press/v119/shankar20a/shankar20a.pdf)

```
dist_est = kernel.est_dist(x_train, 1000)
# See https://github.com/modestyachts/neural_kernels_code/blob/0202718ce8da87f7c1682a6fd87f0caeeaba0859/UCI/UCI.py#L80
# The function est_dist is from 
# https://github.com/modestyachts/neural_kernels_code/blob/0202718ce8da87f7c1682a6fd87f0caeeaba0859/UCI/kernel.py
```

### Jupyter notebooks and tutorials `jupyter_notebooks/`


```
jupyter_notebooks/
├── 01_datasets_summary.ipynb              # display the table of summary
└── 02_LR_TF_example.ipynb                 # Logistic regression in TensorFlow example
```
