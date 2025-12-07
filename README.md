# 🎓 Graduation Project - AI Assistant

A multi-purpose AI application for currency detection, OCR & translation, and image analysis using Flask, YOLO, and Google Generative AI.

## ✨ Features

- **💰 Currency Detection** - Detect and identify currencies in images using YOLO v8
- **📝 OCR & Translation** - Extract text from documents and translate to Arabic using Tesseract
- **🖼️ Image Analysis** - Analyze and describe images using Google Generative AI (Gemini)
- **🎤 Voice Commands** - Control features with voice input (Whisper + DistilBERT)

## 🛠️ Tech Stack

- **Backend**: Flask
- **Computer Vision**: YOLO v8, OpenCV
- **OCR**: Tesseract, pytesseract
- **Speech**: Whisper (OpenAI), SpeechRecognition
- **Translation**: googletrans
- **NLP**: Transformers (DistilBERT), Google Generative AI
- **Deep Learning**: PyTorch, TensorFlow

## 📋 Requirements

- Python 3.7+
- Tesseract OCR (external installation required)
- Google API Key (for image analysis)
- 4GB+ RAM recommended

## 🚀 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/AhmedHelmy778/graduation-project.git
cd graduation-project
```

### 2. Create Virtual Environment (Recommended)

```bash
# Windows
python -m venv venv
venv\Scripts\activate

# Mac/Linux
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Python Dependencies

```bash
pip install -r requirements.txt
```

### 4. Install Tesseract OCR

**Windows:**
1. Download installer: https://github.com/UB-Mannheim/tesseract/wiki
2. Run the installer (default path: `C:\Program Files\Tesseract-OCR`)
3. Add this to top of `app.py`:
```python
import pytesseract
pytesseract.pytesseract.pytesseract_cmd = r'C:\Program Files\Tesseract-OCR\tesseract.exe'
```

**Mac:**
```bash
brew install tesseract
```

**Linux:**
```bash
sudo apt-get install tesseract-ocr
```

### 5. Set Up Environment Variables

Create a `.env` file in project root:

```
gminie_api_key=your_google_generative_ai_api_key
```

Get your API key: https://makersuite.google.com/app/apikey

## 💻 Running the Application

```bash
python app.py
```

Open your browser and go to: **`http://localhost:5000`**

## 📁 Project Structure

```
graduation-project/
├── app.py                      # Main Flask application
├── voice_inference.py          # Voice command processing
├── requirements.txt            # Python dependencies
├── project_model1.pt          # Trained YOLO model
├── .env                       # Environment variables (create this)
├── templates/
│   └── index.html            # Web interface
├── utils/
│   ├── __init__.py
│   ├── currency.py           # Currency detection logic
│   ├── ocr_translate.py      # OCR & translation logic
│   └── api_gminie.py         # Google Generative AI integration
├── uploads/                  # Uploaded files storage (auto-created)
└── README.md                # This file
```

## 🎯 Usage

### 1. Currency Detection
- Click "Upload Image or Document"
- Select an image of currency (bill or coin)
- Click "💰 Detect Currency"
- Results will show the detected currency type and confidence

### 2. Extract Text (OCR & Translate)
- Upload a document or image with text
- Click "📝 Extract Text"
- Text will be extracted and translated to Arabic

### 3. Analyze Image
- Upload any image
- Click "🖼️ Analyze Image"
- AI will provide a detailed description of the image

### 4. Voice Commands
- Use the voice command endpoint to control features with spoken input
- Supported via `/api/voice-command` endpoint

## 🔧 Configuration

### Model Settings

In `utils/currency.py`:
```python
currency_model = YOLO("models/project_model1.pt")
results = currency_model.predict(image_path, conf=0.8, device=device)
```

Adjust `conf=0.8` confidence threshold as needed (0-1).

### Flask Settings

In `app.py`:
```python
app.config['UPLOAD_FOLDER'] = 'uploads/'
ALLOWED_EXTENSIONS = {'png', 'jpg', 'jpeg', 'mp4', 'txt', 'wav', 'mp3', 'ogg', 'flac'}
```

## ⚠️ Troubleshooting

### Tesseract Not Found
```
Error: tesseract is not installed or it's not in your PATH
```
**Solution**: Make sure Tesseract is installed and path in `app.py` is correct.

### Currency Not Detected
- Use a clear, well-lit image of actual money
- Try different angles and lighting
- Model may need retraining with more diverse data

### Google API Errors
- Verify API key in `.env` file
- Ensure Generative AI API is enabled in Google Cloud Console
- Check API quota limits

### Port Already in Use
```bash
# Change port in app.py
app.run(host='0.0.0.0', port=5001, debug=True)
```

### Module Not Found
```bash
# Reinstall dependencies
pip install -r requirements.txt --upgrade
```

## 📊 Model Information

- **YOLO Model**: Custom trained on currency images (`project_model1.pt`)
- **OCR**: Tesseract 5.0+
- **Speech Recognition**: OpenAI Whisper (base model)
- **Classification**: DistilBERT (sequence classification)
- **Image Analysis**: Google Gemini Pro Vision

## 🔒 Security Notes

- Never commit `.env` file to Git
- API keys should be stored in environment variables only
- Uploaded files are stored in `uploads/` folder (consider cleanup)
- Use HTTPS in production

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Commit changes (`git commit -m 'Add improvement'`)
4. Push to branch (`git push origin feature/improvement`)
5. Open a Pull Request

## 📝 License

MIT License - feel free to use this project for educational purposes.

## 👨‍💼 Author

- **Ahmed Helmy** - Graduation Project
- GitHub: [@AhmedHelmy778](https://github.com/AhmedHelmy778)

## 🙏 Acknowledgments

- YOLO v8 by Ultralytics
- Tesseract OCR
- Google Generative AI
- OpenAI Whisper
- Hugging Face Transformers

## 📧 Support

For issues and questions, please open an issue on GitHub: https://github.com/AhmedHelmy778/graduation-project/issues

---

**Happy coding! 🚀**