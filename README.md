# malicious-software-predictor-
Project Workflow Description (File-wise)
cnmodal.py
This script performs data preprocessing and model training. It loads the UNSW-NB15 dataset, applies label encoding to categorical features, and normalizes numerical features using MinMaxScaler. The dataset is then split into training and test sets. Three base models are defined: Random Forest, Gradient Boosting Classifier, and MLPClassifier. These models are combined using a StackingClassifier, which is trained on the data. The final ensemble model is saved using joblib for later use in prediction.

flaskcn.py
This file implements the backend API using Flask. It loads the trained ensemble model from the serialized joblib file. It defines a route (/predict) that accepts POST requests containing input features. The input data is parsed, reshaped, and passed to the model for prediction. The result is returned as a response indicating whether the software is classified as malicious or benign.

cnui.py
This file provides a simple user interface connected to the Flask backend. It collects user input for various malware detection features, sends this data to the /predict endpoint via an AJAX POST request, and displays the prediction result on the web page. It links the frontend and backend, enabling real-time interaction for malware classification.

This structure ensures a modular pipeline:

cnmodal.py handles training and model preparation.

flaskcn.py exposes the model for real-time use.

cnui.py allows user interaction with the system through a web-based UI.
