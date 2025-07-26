# Titanic_MLops

## Description
Greetings!!! This is a very basic ML pipeline to update a model every time there's new training data.
This means that the model will iteratively get retrained to account for new data.

## To replicate the project on your system follow the Following steps.

## ✅ Step 1: Setting up the Environment 
### 🧱 Folder Structure
Create a clean Project Folder
```
titanic-mlops/
├── data/
│   └── train.csv
├── src/
│   └── train.py
├── models/
└── requirements.txt
```

## 🔁 Step 2: Running the following commands in the terminal
### 1. Initiliazing GIT + DVC (Data Version Control)
```
cd titanic-mlops
git init
dvc init
```
### 2. Tracking the data with DVC
```
dvc add data/train.csv
git add data/train.csv .gitignore
git commit -m "Track Titanic dataset with DVC"
```
Now that
* Our data is tracked with DVC
* Code is versioned with GIT
* We have the working training script

### 3. Tracking the model with DVC
```
dvc add models/model.pkl
git add models/model.pkl.dvc
git commit -m "Track trained model with DVC"
```

### 4. Defining DVC stage for training
```
dvc stage add -n train_model \
  -d src/train.py \
  -d data/train.csv \
  -o models/model.pkl \
  python src/train.py --input data/train.csv --output models/model.pkl
```

### 5. Run the pipeline
```
dvc repro
```

### 6. Commit the pipeline definition
```
git add dvc.yaml dvc.lock .gitignore
git commit -m "Add training stage with DVC for training"
```


Thank You!! I hope that you are able to replicate the pipeline with ease.
The training script contains the configuration to track the model metrics with the help of mlflow.
To view the model performance and iterations, Run the following command in the terminal.
```
mlflow ui
```

## About Me:
Hi I'm Vansh Mahajan, An aspiring Data Scientist. You can connect with me on my Socials below:
<br><br>
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/vanshmahajan55/)
