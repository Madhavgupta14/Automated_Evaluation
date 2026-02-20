# Automated Evaluation - TVS Credit IT Challenge

An intelligent web application for automated vehicle evaluation and price prediction using machine learning. This project combines a React-based frontend with a Node.js/Express backend and Python ML models to predict car prices based on various features.

## 🎯 Project Overview

The Automated Evaluation system is designed to:
- Collect vehicle information (brand, model, location, features)
- Process multi-view images (front, back, left, right views)
- Predict vehicle prices using advanced ML/DL models
- Compare ML and Deep Learning model performances
- Provide user authentication and data management

## 📁 Project Structure

```
Automated_Evaluation/
├── client/                 # React Frontend Application
│   ├── public/            # Static assets
│   ├── src/
│   │   ├── components/    # React Components
│   │   │   ├── Home.js    # Home page
│   │   │   ├── Login.js   # User login
│   │   │   ├── Registeration.js  # User registration
│   │   │   ├── Navbar.js  # Navigation bar
│   │   │   └── Logout.js  # Logout functionality
│   │   ├── App.js         # Main App component
│   │   └── index.js       # Entry point
│   ├── package.json
│   └── package-lock.json
│
└── server/                 # Node.js/Express Backend
    ├── middleware/        # Custom middleware
    ├── model/             # Database schemas
    │   └── userSchema.js  # User model
    ├── router/            # API routes
    │   └── auth.js        # Authentication routes
    ├── db/                # Database configuration
    │   └── Mongoose_Connection.js
    ├── app.js             # Express server
    ├── ML_Score.py        # ML model training/prediction
    ├── Non_ML_Score.py    # Non-ML scoring methods
    ├── Comparison_ML_DL.py  # ML vs DL comparison
    ├── Audio_Download_Compare.py  # Audio processing
    ├── Image_Download_Compare.py   # Image processing
    ├── Csv_Size.py        # CSV utility
    ├── S3_Front_View.js   # AWS S3 upload - Front view
    ├── S3_Back_View.js    # AWS S3 upload - Back view
    ├── S3_Left_View.js    # AWS S3 upload - Left view
    ├── S3_Right_View.js   # AWS S3 upload - Right view
    ├── S3_Accelarate.js   # AWS S3 acceleration feature
    ├── S3_Deaccelarate.js # AWS S3 deacceleration feature
    ├── Car_Price_Predictor/  # XGBoost model
    ├── *.csv              # Data files
    ├── config.env         # Environment variables
    ├── package.json
    └── package.json
```

## 🚀 Key Features

### Frontend (React)
- **Authentication System**: User login and registration
- **Responsive UI**: Bootstrap-based responsive design
- **Real-time Data Submission**: Form-based vehicle information entry
- **Image Upload**: Multi-view image upload (front, back, left, right)
- **Navigation**: Persistent navigation bar with user options

### Backend (Node.js/Express)
- **REST API**: Express-based API endpoints
- **Authentication**: JWT-based user authentication
- **File Upload**: Multer for file handling
- **AWS S3 Integration**: Direct image uploads to S3 buckets
- **Database**: MongoDB for user and data persistence
- **CORS Support**: Cross-Origin Resource Sharing enabled

### Machine Learning
- **Price Prediction**: XGBoost regressor model for car price prediction
- **Model Comparison**: ML vs Deep Learning model performance analysis
- **Data Preprocessing**: Target encoding, standard scaling, feature engineering
- **Data Files**:
  - `Synthetic_entries.csv`: Training data with synthetic entries
  - `Manual_entries.csv`: Manually collected vehicle data
  - `With_header.csv` / `Without_header.csv`: Formatted data files

## 🛠 Tech Stack

### Frontend
- **React** 18.2.0
- **React Router** 5.2.0
- **Bootstrap** 5.2.2
- **Axios** 1.1.3 (HTTP client)
- **React Google Drive Picker** (for file selection)

### Backend
- **Node.js & Express** 4.18.2
- **MongoDB** with Mongoose 6.6.5
- **AWS SDK** 2.1244.0
- **JWT** (JSON Web Tokens) 8.5.1
- **Bcrypt** for password hashing
- **Multer** for file uploads

### Data Science & ML
- **XGBoost**: Gradient boosting for price prediction
- **Scikit-learn**: Machine learning toolkit
- **Keras/TensorFlow**: Deep Learning models
- **Pandas**: Data manipulation
- **NumPy**: Numerical computing
- **Matplotlib & Seaborn**: Data visualization

## 📊 Models & Algorithms

1. **XGBoost Regressor**
   - Hyperparameter tuning via GridSearchCV
   - Parameters: `n_estimators`, `max_depth`, `eta`
   - Used for car price prediction

2. **ML vs DL Comparison**
   - Random Forest Regressor
   - Linear Regression
   - XGBoost
   - Keras Sequential Neural Network
   - Metrics: MSE, RMSE, MAE, MAPE

3. **Target Encoding**
   - Applied to categorical features: Brand, Model, Location

## 🔌 API Endpoints

### S3 Upload Endpoints
- `POST /s3front` - Generate S3 URL for front view
- `POST /s3back` - Generate S3 URL for back view
- `POST /s3left` - Generate S3 URL for left view
- `POST /s3right` - Generate S3 URL for right view
- `POST /s3accelarate` - Upload with S3 acceleration
- `POST /s3deaccelarate` - Upload without acceleration

### Authentication (router/auth.js)
- User registration and login endpoints
- JWT token management

## 🔐 Security Features

- **Password Hashing**: Bcryptjs for secure password storage
- **JWT Authentication**: Token-based user authentication
- **Cookie Parser**: Secure cookie handling
- **CORS**: Controlled cross-origin requests
- **Environment Variables**: Sensitive data in `config.env`

## 📦 Installation & Setup

### Prerequisites
- Node.js (v14+)
- Python (v3.7+)
- MongoDB account
- AWS S3 bucket credentials

### Frontend Setup
```bash
cd client
npm install
npm start
```

### Backend Setup
```bash
cd server
npm install
node app.js
# Server runs on http://localhost:5000
```

### Python ML Models
```bash
pip install pandas numpy scikit-learn xgboost keras matplotlib seaborn category-encoders
```

## ⚙️ Configuration

Create a `config.env` file in the server directory with:
```
MONGODB_URL=<your_mongodb_connection_string>
JWT_SECRET=<your_jwt_secret>
AWS_ACCESS_KEY_ID=<your_aws_key>
AWS_SECRET_ACCESS_KEY=<your_aws_secret>
AWS_S3_BUCKET=<your_bucket_name>
```

## 🎓 Data Processing Pipeline

1. **Data Collection**: CSV files with vehicle information
2. **Preprocessing**: 
   - Drop unnecessary columns
   - Encode categorical features (Brand, Model, Location)
   - Scale numerical features
3. **Model Training**: 
   - Train-test split (80-20)
   - Hyperparameter tuning
   - Model evaluation
4. **Prediction**: 
   - Load trained model
   - Process input features
   - Generate price predictions

## 📈 Performance Metrics

The project evaluates models using:
- **RMSE** (Root Mean Squared Error)
- **MSE** (Mean Squared Error)
- **MAE** (Mean Absolute Error)
- **MAPE** (Mean Absolute Percentage Error)

## 🤝 Contributing

This project was created as part of TVS Credit IT Challenge.

## 📝 Notes

- Ensure all dependencies are installed before running
- Configure MongoDB connection in `db/Mongoose_Connection.js`
- Set up AWS S3 credentials in `config.env`
- The trained XGBoost model is stored in `Car_Price_Predictor` directory
- Frontend runs on `http://localhost:3000`
- Backend API runs on `http://localhost:5000`

## 📄 License

ISC License

## 👤 Author

Harsh Gupta
Keshav Gupta
Madhav Gupta

---


