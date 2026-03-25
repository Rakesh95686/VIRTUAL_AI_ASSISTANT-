# 🧠 MedicaAI - Virtual AI Health Assistant

**Your AI Health Companion** - A web-based application that uses **Machine Learning** and **Flask** to predict diseases based on user input symptoms.

It provides the **disease description**, **related symptoms**, and **precautionary measures** to take. The assistant acts like a chatbot that interacts with users in real-time through a clean web interface.

---

## 🚀 Features

- ✅ Predict diseases using a pre-trained Random Forest model
- 🧠 Respond like a chatbot through the frontend interface
- 📊 Displays disease description, symptoms, and precautions
- 🔍 Fuzzy symptom matching - automatically corrects misspelled symptoms
- 📈 Confidence scoring with alternative diagnoses
- ⚖️ Symptom severity analysis (1-7 scale)
- 🌐 Fully functional Flask backend with RESTful API
- 💬 Easy to customize and expand for more features

---

## 🧰 Tech Stack

| Component         | Technology Used              |
|-------------------|-------------------------------|
| Frontend          | HTML, CSS, JavaScript         |
| Backend           | Python, Flask                 |
| Machine Learning  | scikit-learn, Random Forest   |
| Data Processing   | pandas, NumPy                 |
| Model Persistence | joblib                        |
| Deployment        | Render / Localhost            |

---

## 📂 Project Structure

```
VIRTUAL_AI_ASSISTANT-main/
├── app.py                      # Main Flask server file
├── predict_disease.py          # ML prediction logic
├── train_model.py              # Script to train and save model
├── requirements.txt            # Required Python packages
├── render.yaml                 # Render deployment config
├── README.md                   # This file
│
├── dataset/                    # CSV files for training/prediction
│   ├── dataset.csv             # Main symptom-disease dataset
│   ├── symptom_description.csv # Disease descriptions
│   ├── symptom_precaution.csv  # Precautionary measures
│   └── symptom_severity.csv    # Symptom severity weights
│
├── models/                     # Pre-trained ML models
│   ├── disease_rf_model.joblib
│   ├── feature_importance.joblib
│   ├── symptom_list.joblib
│   └── symptom_mapping.joblib
│
├── static/                     # CSS, JS, and static assets
│   ├── style.css
│   ├── script.js
│   └── favicon.ico
│
└── templates/                  # HTML templates
    └── index.html
```

---

## 🛠️ Installation & Setup

### 1️⃣ Clone or Download

```bash
git clone https://github.com/your-username/medicaai.git
cd medicaai
```

### 2️⃣ Create Virtual Environment (Recommended)

```bash
python -m venv .venv

# Activate:
# On Windows:
.venv\Scripts\activate

# On macOS/Linux:
source .venv/bin/activate
```

### 3️⃣ Install Required Packages

```bash
pip install -r requirements.txt
```

### 4️⃣ Train the Model (Optional - pre-trained models included)

```bash
python train_model.py
```

This will generate updated model files in the `models/` folder.

### 5️⃣ Run the Flask App

```bash
python app.py
```

The server will start at: 👉 **http://127.0.0.1:5000** or **http://127.0.0.1:10000**

Open this URL in your browser to use the assistant.

---

## 🌐 API Endpoints

### `GET /`
Returns the main web interface

### `POST /api/predict`
Predicts disease based on symptoms

**Request Body:**
```json
{
  "symptoms": "fever, cough, headache"
}
```

**Response:**
```json
{
  "status": "success",
  "messages": [...],
  "raw_results": {
    "top_prediction": {
      "disease": "Common Cold",
      "probability": 0.85,
      "description": "...",
      "precautions": [...]
    },
    "alternative_predictions": [...],
    "symptom_details": [...]
  }
}
```

### `GET /api/symptoms`
Returns list of all recognized symptoms

---

## 🔧 Fixing Common Issues

### CSS Not Loading?

If your CSS is not loading, check your `index.html` inside `templates/` and make sure the CSS is linked like this:

```html
<link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
```

**Do not use** relative paths like `static/style.css` — Flask handles this through `url_for`.

Also, try hard refreshing the browser with **Ctrl + Shift + R** (Windows/Linux) or **Cmd + Shift + R** (Mac).

### Port Already in Use?

If port 10000 is busy, you can change it:

```bash
PORT=8080 python app.py
```

Or modify the port in `app.py`:

```python
port = int(os.environ.get('PORT', 8080))
```

---

## 🧠 Model Training Details

The Random Forest classifier is trained with:
- **Hyperparameter tuning** using GridSearchCV
- **Stratified K-Fold cross-validation** (5 folds)
- **Class balancing** to handle imbalanced disease distributions
- **Feature importance analysis** for interpretability

**Model Performance:**
- Training uses 80/20 train-test split
- Achieves high accuracy on validation set
- Supports prediction of 40+ diseases
- Handles 130+ unique symptoms

---

## 💻 Command Line Usage

You can also use the predictor from command line:

```bash
# Interactive mode
python predict_disease.py --interactive

# Single prediction
python predict_disease.py --symptoms "fever, cough, fatigue"
```

---

## 🚀 Deployment

### Deploy to Render

1. Push your code to GitHub
2. Connect your repository to Render
3. Render will automatically detect `render.yaml`
4. Your app will be deployed at `https://your-app.onrender.com`

The `render.yaml` file is already configured for deployment.

---

## 📝 Notes

- ⚠️ **Disclaimer**: This is an educational project. Always consult healthcare professionals for medical advice.
- 🔒 **Privacy**: No user data is stored or logged
- 🧪 **Accuracy**: Predictions are based on training data and may not cover all medical conditions
- 📚 **Dataset**: Uses publicly available symptom-disease datasets

---

## 🙌 Contribution

Feel free to:
- Report bugs 🐛
- Suggest features ✨
- Improve the model or frontend 🎨
- Submit pull requests 🔧

---

## 📄 License

This project is for educational and personal use. You can modify and use it as per your needs.

---

## 👨‍💻 Author

**Developed by Rakesh Kumar Lohani**
- 📅 B.Tech CSE Student
- 💡 Passionate about AI & Web Development
- 🌐 [Rakesh965686](https://github.com/Rakesh95686)

---

**⭐ If you find this project helpful, please star the repository!**
