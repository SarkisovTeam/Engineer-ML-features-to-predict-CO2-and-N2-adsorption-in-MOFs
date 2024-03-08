# Supplementary information for 
### *Engineering Machine Learning features to predict adsorption of carbon dioxide and nitrogen in metal-organic frameworks*

*Zijun Deng, Lev Sarkisov*


This repository contains the scripts for feature calculation and the machine learning (ML) models to the article *Engineering Machine Learning features to predict adsorption of carbon dioxide and nitrogen in metal-organic frameworks* by Zijun Deng and Lev Sarkisov. 


Note:
-----
The scripts are provided as-is, and are not guaranteed to work without the required dependencies or with different structure from that used in our work. If you have any questions, please contact the corresponding author of the article.

##	How to compute geometric features
Requirement: Zeo++
1.	Compute large cavity diameter(LCD, angstrom), density(g/cm^3), surface area(SA, m^2/g), and accessable volume(AV, m^3/g) for testing structures, using Zeo++. See the link for details: https://www.zeoplusplus.org/examples.html
2.	Put geometric features into the the file "ML_model/CO2/x_test.csv" or "ML_model/N2/x_test.csv".


##	How to compute Henry's law constant
Requirement: RASPA
1.	Make sure testing structures are with partial atomic charges (PACMOF packge is recommended in partial charge calculation).
2.	Compute Henry's law constant using RASPA. Force field and input files are provided in the folder "feature_calculation/henrys_law_constant".  See the link for more details: https://github.com/iRASPA/RASPA2/blob/master/Docs/raspa.pdf
3.	Put Henry's law constant into the file "ML_model/CO2/x_test.csv" or "ML_model/N2/x_test.csv".


##	How to compute energy features
Requirement: Jupyter Notebook, Python with packages - NumPy, Pandas, SciPy, ASE
1.	Make sure the testing structure are with partial atomic charges (PACMOF packge is recommended in partial charge calculation). Copy the cif file to the folder “feature_calculation/energy_features/CO2”
2.	Compute energy features by running the script “feature_calculation/energy_features/CO2/surface_feature_calculation.ipynb” in Jupyter Notebook
3.	Put energy features into the file "ML_model/CO2/x_test.csv", after Henry's law constant.


##	How to predict adsorption isotherm using ML models
Requirement: Jupyter Notebook, Python with packages - NumPy, Pandas, Scikit-learn, XGBoost, Pickle, Joblib
1.	Go to the directory "ML_model/CO2" or "ML_model/N2". predict adsorption isotherm by running the script “predict_adsorption.ipynb” in Jupyter Notebook
2.	Collect adsorption loadings at [0.001bar, 0.002bar, 0.005bar, 0.01bar, 0.02bar, 0.05bar, 0.1bar, 0.2bar, 0.5bar, 1bar] in "y_predict.txt"


##	How to train new ML models
Requirement: Jupyter Notebook, Python with packages - NumPy, Pandas, Scikit-learn, XGBoost, Pickle, Joblib

1.  Go to the directory "ML_model/CO2/training" or "ML_model/N2/training". Put training data into the file "train.csv".
2.	Train ML models by running the script “train.ipynb” in Jupyter Notebook
3.	Collect the model files "scaler_3.pkl" and "model_3.pkl"
