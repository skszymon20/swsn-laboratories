## Taste Prediction
This repository is used to predict different tastes based on molecules shapes.

## The data Sources:
we used 2 datasets:
 - FlavorDB2: https://cosylab.iiitd.edu.in/flavordb2 -> we manaully scraped the content of the website (scraping procedure is in flavorDB.ipynb)
 - ChemTastesDB: https://zenodo.org/record/5747393#.Y4RkSXbMK5c -> It consists of 2947 rows

FlacordDB2 was much bigger source of data.
The Dataset Analysis preliminary analysis can be viewed in flavorDB.ipynb

## New Dataset
We created dataset.csv out of FlavorDB2 and ChemTastesDB in such a way that:
 - we dropped duplicates
 - we left only 3 tastes

The whole dataset consists of 13821 rows in following proportions:
 - sweet: 11710
 - bitter: 1775
 - odorless: 336

For details view preprocess_and_create_dataset.ipynb

## Classical ML Methods Test
Preprocessing:
 - We one-hot encoded smiles (chemical structures of molecules)

We performed dataset split:
 - 80% of data were taken as train set
 - 20% of data were taken as test set
Morover, we oversampled both bitter and odorless tastes.

We tested 2 classical methods for classification task:
 - Random Forest Classifier
 - KNeighbors Classifier

We obtained following results:
 - For RandomForest: 
   - 84.33% Accuracy with very good predictions mostly on sweet taste.
    - FScores were following:
        - 0.91 for sweet class
        - 0.60 for bitter class
        - 0.34 for odorless class
 - for KNN Classifier:
   - 83.68% Accuracy with very good predictions mostly on sweet taste.
    - FScores were following:
        - 0.91 for sweet class
        - 0.61 for bitter class
        - 0.30 for odorless class

Both methods were taken from sklearn library (https://scikit-learn.org/stable/).

For details view: smiles_to_onehot.ipynb

## Neural Networks TEST
We percfomed stratified split od the data. Train dataset consted of ~86% of the data while test dataset costed of ~14% of the data. We used only sweet and bitter tastes.

We defined custom network which consited of Graph Convolutional Blocks (GCN-s), each one followed by ReLU, with ending Linear Layer to output 2 classes that we wanted to predict. As a loss function we used CrossEntropyLoss which is standard for classification purposes.

Results:
 - we trained for 100 epochs    
 - we achieved best accuracy at the level of 91.76%
 - fscores for both classes were as follows:
    - for sweet class: 0.95
    - for bitter class: 0.68

For details view graph_smiles.ipynb

## Additional test for reference
We tested once again RandomForest Classifier and KNN Classifier for 2 classes case to obtain results:
 - For RandomForest:
     - 86.25% Accuracy with very good predictions mostly on sweet taste.
     - Fscores were following:
         - 0.92 for sweet class
         - 0.62 for bitter class
 - For KNN:
     - 87.43% Accuracy with very good predictions mostly on sweet taste.
     - Fscorews were following:
         - 0.92 for sweet class
         - 0.64 for bitter class

For details view our notebook graph_smiles.ipynb

## Authors
 - Antoni Klorek, email contact: antekk2000@gmail.com
 - Szymon Skwarek, email contact: skszymon20@gmail.com