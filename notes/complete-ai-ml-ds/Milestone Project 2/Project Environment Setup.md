Steps in starting a new project
1. Create project folder
2. Get data ready
3. Create an environment
4. Launch a Jupyter notebook
	1. Ensure we can import our tools

Create folder
```bash
cd ~/professional/projects/complete-ai-ml-ds
mkdir -p bulldozer-price/data
```

Download data from Kaggle
- This action failed for me; however, I had downloaded the data previously
- Unzipped to `bulldozer-price/data/bluebook-for-bulldozers`

Create an environment using `conda`
```bash
conda create --name bulldozer-price --clone heart-disease-project
cd bulldozer-price
conda env export -f environment.yaml
```

Create PyCharm project from existing sources
- `~/professional/projects/complete-ai-ml-ds/bulldozer-price`
- Change `conda` interpreter 
	- From `base`
	- To `bulldozer-price`
- Rename 
	- File `sample.ipynb`
	- To ``