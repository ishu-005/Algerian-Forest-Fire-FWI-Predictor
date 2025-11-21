Algerian Forest Fire — FWI Predictor

A Flask web app that predicts the Fire Weather Index (FWI) for the Algerian Forest Fires dataset using a trained Ridge regression model. The app loads a saved scaler and ridge model (models/scaler.pkle, models/ridge.pkle) and returns a numeric FWI prediction from user-provided weather/fire-index inputs.

    
What this app predicts
Target variable: FWI (Fire Weather Index). The notebooks show y = df['FWI'] and model training used multiple regression methods and saved a ridge model.
Inputs (form fields expected by the web UI)


When calling the prediction route, the app expects these numeric inputs (order used by the scaler/model): 
Temperature  
RH (Relative Humidity) 
WS / Ws (Wind Speed)    
Rain   
FFMC  
DMC  
ISI  
Classes (encoded: not fire → 0, fire → 1 in preprocessing)   
Region (numeric region code)    


The app transforms input with standard_scaler.transform([[Temperature,RH,WS,Rain,FFMC,DMC,ISI,Classes,Region]]) and runs ridge_model.predict(...).  


Project structure   

├── application.py                             # Flask app (routes: / and /predictdata)   
├── requirement.txt                            # Python dependencies   
├── dataset/     
│   ├── Algerian_forest_fires_cleaned_dataset.csv     
│   └── Algerian_forest_fires_dataset_UPDATE.csv     
├── models/   
│   ├── ridge.pkle                             # trained Ridge regression model   
│   └── scaler.pkle                            # StandardScaler used for preprocessing    
├── notebook/   
│   ├── algerianforestfires.ipynb              # EDA and cleaning    
│   └── modelTraning.ipynb                     # model training & evaluation (train/test split, model selection)    
└── templates/   
    ├── home.html   
    └── index.html   
