H2 start a new project

Create project 
```bash
mkdir heart-disease-project
cd heart-disease-project
```

Create  `conda` environment
```bash
conda create -n heart-disease-project numpy matplotlib pandas scikit-learn jupyterlab ipython toolz
```

Video creates environment by
```bash
conda activate
conda activate sample-project
cd sample-project
conda env export > environment.yml
conda deactivate
cd ../heart-disease-project
conda env create --prefix ./env -f ../environment.yml
```

Activate project
```bash
conda activate heart-disease-project
```

Copy data from `sample-project`
```bash
cd heart-disease-project
mkdir data
cp ../sample-project/data/heart-disease.csv ./data/
```

Now its time to create a notebook and start performing data analysis
