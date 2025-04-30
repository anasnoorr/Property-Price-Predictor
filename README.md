# Property-Price-Predictor

This project predicts property prices using a machine learning model built with Scikit-learn and XGBoost. It takes inputs like property type, location, city, bedrooms, baths, area, and purpose, and returns an estimated price range.

Features Used
Categorical: property_type, location, city, purpose

Numerical: bedrooms, baths, Area_in_Marla

How It Works
Data is preprocessed using OneHotEncoder and ColumnTransformer.

Target prices are log-transformed for better prediction accuracy.

Model is trained with XGBRegressor and saved using joblib.

A prediction script loads the model and estimates the price range.

# --- Sample Prediction ---
sample = pd.DataFrame({
    'property_type': ['House'],
    'location': ['Abdullah Garden'],
    'city': ['Islamabad'],
    'baths': [2],
    'purpose': ['For Sale'],
    'bedrooms': [2],
    'Area_in_Marla': [4]
})

predicted_log_price = model.predict(sample)[0]
predicted_price = np.exp(predicted_log_price)

low_price = predicted_price * 0.90
high_price = predicted_price * 1.1

print(f"Predicted Price Range: {low_price:,.0f} - {high_price:,.0f} PKR")


OUTPUT : Predicted Price Range: 4,506,778 - 5,508,285 PKR
