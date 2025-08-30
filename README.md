# Face Mask Detection Project

A comprehensive AI-powered face mask detection system built with TensorFlow and Flask. This project can detect whether a person is wearing a face mask or not using deep learning techniques.

## 🚀 Features

- **Deep Learning Model**: CNN-based model trained on a large dataset of masked/unmasked faces
- **Web Interface**: Modern, responsive web application with drag-and-drop image upload
- **Real-time Webcam**: Live webcam integration for instant mask detection
- **High Accuracy**: Achieves over 94% accuracy on test data
- **Multiple Input Methods**: Support for image uploads and webcam capture
- **Confidence Scores**: Detailed probability scores for predictions
- **Statistics Tracking**: Real-time tracking of detection results
- **Deployment Ready**: Easy to deploy on various platforms

## 📋 Requirements

- Python 3.8+
- TensorFlow 2.15.0
- OpenCV 4.8+
- Flask 2.3+
- Other dependencies listed in `requirements.txt`

## 🛠️ Installation

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd Face_mask_detection_proj
   ```

2. **Create a virtual environment (recommended)**
   ```bash
   python -m venv venv
   
   # On Windows
   venv\Scripts\activate
   
   # On macOS/Linux
   source venv/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

## 📊 Dataset Setup

The project uses the Face Mask Dataset from Kaggle. You have two options:

### Option 1: Manual Download (Recommended)
1. Visit: [Face Mask Dataset](https://www.kaggle.com/datasets/omkargurav/face-mask-dataset)
2. Download the dataset
3. Extract it to the `data/` directory
4. Ensure you have the following structure:
   ```
   data/
   ├── with_mask/
   │   ├── with_mask_1.jpg
   │   ├── with_mask_2.jpg
   │   └── ...
   └── without_mask/
       ├── without_mask_1.jpg
       ├── without_mask_2.jpg
       └── ...
   ```

### Option 2: Kaggle CLI
1. Install Kaggle CLI: `pip install kaggle`
2. Configure your Kaggle API credentials
3. Run: `kaggle datasets download -d omkargurav/face-mask-dataset`
4. Extract the downloaded file

## 🎯 Training the Model

1. **Run the training script**
   ```bash
   python train_model.py
   ```

   This will:
   - Load and preprocess the dataset
   - Create and train the CNN model
   - Save the trained model to `models/face_mask_detection_model.h5`
   - Generate training history plots in `plots/` directory

2. **Training parameters** (modify in `train_model.py`):
   - Epochs: 10 (default)
   - Batch size: 32
   - Image size: 128x128
   - Test split: 20%

## 🌐 Running the Web Application

1. **Start the Flask app**
   ```bash
   python app.py
   ```

2. **Open your browser**
   Navigate to: `http://localhost:5000`

3. **Features available**:
   - **Image Upload**: Drag & drop or browse for images
   - **Webcam**: Real-time camera detection
   - **Statistics**: Track detection results
   - **Responsive Design**: Works on desktop and mobile

## 🔍 Standalone Prediction

Use the prediction script for testing without the web interface:

```bash
# Basic prediction
python predict.py --image path/to/your/image.jpg

# Display results with image overlay
python predict.py --image path/to/your/image.jpg --display

# Use custom model path
python predict.py --model path/to/model.h5 --image path/to/your/image.jpg
```

## 📁 Project Structure

```
Face_mask_detection_proj/
├── app.py                          # Flask web application
├── train_model.py                  # Model training script
├── predict.py                      # Standalone prediction script
├── requirements.txt                # Python dependencies
├── README.md                       # This file
├── templates/
│   └── index.html                 # Web interface template
├── models/                         # Trained models (created after training)
├── data/                          # Dataset directory
├── plots/                         # Training plots (created after training)
└── uploads/                       # Temporary upload directory
```

## 🚀 Deployment

### Local Development
```bash
python app.py
```

### Production Deployment

1. **Using Gunicorn**
   ```bash
   pip install gunicorn
   gunicorn -w 4 -b 0.0.0.0:5000 app:app
   ```

2. **Docker Deployment**
   ```dockerfile
   FROM python:3.9-slim
   WORKDIR /app
   COPY requirements.txt .
   RUN pip install -r requirements.txt
   COPY . .
   EXPOSE 5000
   CMD ["gunicorn", "-w", "4", "-b", "0.0.0.0:5000", "app:app"]
   ```

3. **Cloud Platforms**
   - **Heroku**: Add `Procfile` with `web: gunicorn app:app`
   - **AWS**: Use Elastic Beanstalk or EC2
   - **Google Cloud**: Use App Engine or Compute Engine
   - **Azure**: Use App Service

## 📊 Model Performance

- **Training Accuracy**: ~97%
- **Validation Accuracy**: ~95%
- **Test Accuracy**: ~94%
- **Model Architecture**: CNN with 2 convolutional layers
- **Input Size**: 128x128x3 RGB images
- **Output**: Binary classification (Mask/No Mask)

## 🎨 Customization

### Model Architecture
Modify the `create_model()` function in `train_model.py` to:
- Change layer configurations
- Add more layers
- Modify activation functions
- Adjust dropout rates

### Training Parameters
Adjust in `train_model.py`:
- Number of epochs
- Batch size
- Learning rate
- Validation split

### Web Interface
Customize `templates/index.html`:
- Colors and styling
- Layout modifications
- Additional features
- Mobile responsiveness

## 🔧 Troubleshooting

### Common Issues

1. **Model not loading**
   - Ensure you've trained the model first
   - Check the model file path
   - Verify TensorFlow version compatibility

2. **Dataset not found**
   - Download and extract the dataset to `data/` directory
   - Verify folder structure matches requirements

3. **Dependencies issues**
   - Use the exact versions in `requirements.txt`
   - Create a fresh virtual environment
   - Update pip: `pip install --upgrade pip`

4. **Webcam not working**
   - Check camera permissions
   - Ensure HTTPS for production (required for webcam)
   - Test with different browsers

### Performance Optimization

1. **Model inference speed**
   - Use TensorFlow Lite for mobile deployment
   - Optimize image preprocessing
   - Consider model quantization

2. **Memory usage**
   - Reduce batch size during training
   - Use image generators for large datasets
   - Implement proper cleanup in web app

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🙏 Acknowledgments

- Dataset: [Face Mask Dataset](https://www.kaggle.com/datasets/omkargurav/face-mask-dataset) by Omkar Gurav
- TensorFlow and Keras for deep learning framework
- Flask for web framework
- OpenCV for computer vision

## 📞 Support

For questions or issues:
1. Check the troubleshooting section
2. Review the code comments
3. Open an issue on GitHub
4. Contact the development team

---

**Happy Mask Detection! 😷✨**
