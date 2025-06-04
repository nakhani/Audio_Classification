# README: Training and Preprocessing singer Data with TensorFlow

Singer Classification with TensorFlow & Telegram Bot This project utilizes TensorFlow to classify singers based on custom-generated audio data. It includes advanced preprocessing to enhance accuracy and a Telegram bot for interactive recognition. Users can explore, test, and contribute to refining the model.

---
## 1. Singer Selection & Voice Extraction

- Choose **5 Persian singers** (e.g., Mohsen Chavoshi, Mohsen Yeganeh, Ebi, ...).
- Collect **2 songs** from each singer.
- Use **Spleeter** in Google Colab to extract the singer's voice from music:

    - Installs **FFmpeg** and **Spleeter**
    - Loads audio files from `raw_data`
    - Creates a `vocals` directory for output
    - Uses Spleeter (`2stems` model) to split vocals & accompaniment
    - Saves extracted vocals in `/dataset/vocals/`

---

## 2. Preprocessing Audio Data

Before training, the raw audio data needs to be processed to ensure uniformity and compatibility with the model. Here's how the preprocessing works:

### **Input**
Audio files located in a folder named `vocals`.

### **Processing Steps**
1. **Merge Files**:
   - If audio files have similar names (e.g., `file_1.wav` and `file_2.wav`), they are merged.
   - The merged file is saved with the common prefix (e.g., `file`).
   
2. **Standardization**:
   - Set sample width to **16 bits (2 bytes)**.
   - Resample the audio to **48 kHz**.
   - Convert all audio to **mono** (single channel).
   
3. **Silence Removal**:
   - Split the audio on silent segments (minimum silence length: **3 seconds**, silence threshold: **-40 dB**).
   
4. **Chunking**:
   - Break audio into 1-second chunks (or longer).
   - Export chunks as WAV files into a folder structure under `final_data_singer`.

### **Output**
Processed audio chunks saved in subfolders, ready for training.

---

## 3. Training the Model

Using the preprocessed audio data, a deep learning model is trained. 

### **Loading Data**
- Use TensorFlow's `audio_dataset_from_directory` to load audio files from `final_data_singer`.
- Split the dataset into training (80%) and validation (20%).
- Each audio file is converted into sequences of length **48,000 samples**.

### **Model Architecture**
A **1D Convolutional Neural Network (CNN)** with the following layers:
- **Conv1D**: For extracting local temporal patterns from the audio.
- **BatchNormalization**: To stabilize training.
- **MaxPooling1D**: For down-sampling.
- **Dropout**: For regularization and avoiding overfitting.
- **GlobalAveragePooling1D**: To reduce feature maps into a single vector.
- **Dense Layers**: Fully connected layers with L2 regularization and `ReLU` activation.
- **Softmax Output**: For classifying into 16 distinct classes.

### **Optimizer and Loss**
- **Optimizer**: Adam with learning rate decay.
- **Loss Function**: Categorical cross-entropy.

### **Training Parameters**
- **Early Stopping**: Stops training if validation loss doesn't improve for 5 epochs.
- **Learning Rate Reduction**: Reduces the learning rate if validation loss plateaus for 3 epochs.
- **Epochs**: 20.

---

## 4. Model Evaluation

### **Metrics During Training**
- The accuracy and loss are plotted for training and validation sets.

  <img src="Accuracy.png" width = "300">

  <img src="Loss.png" width = "300">

- Metrics for the final epoch are printed, including:

 | Epoch | Train Accuracy | Validation Accuracy | Train Loss | Validation Loss |
 |-------|----------------|---------------------|------------|-----------------|
 |  20   | 0.86           | 0.88                | 0.51       | 0.42            |
 


---

## 5. Predicting Audio Classes

A custom function is provided to make predictions on new audio files.

### **Steps**
1. Extract the vocal of song.
2. Convert the audio file into a WAV format if it's not already.
3. Load and preprocess the audio (pad/truncate to 48,000 samples).
4. Pass the audio to the trained model to predict its class.

### **Example Usage**
```python
audio_path = "example_audio.wav"  # Path to the audio file
predicted_class = predict_audio(audio_path)
print(f"Predicted class: {predicted_class}")
```
---
### 📌 Resources
- **📥 Download persian singer classification model**: [Download Here](https://drive.google.com/file/d/1m46YXM19L27skKjfpq0N7Lj3lThu11DW/view?usp=sharing) 

---

## How to Run the Code
1. Clone the repository:

```
https://github.com/nakhani/Audio_Classification/tree/ce200d15a7657e612600b9b6b1f689f3b2d0f983/singer%20version
```

2. Navigate to the directory:

```
   Introduction to singer version
```

4. Run the assignments:
  
```
jupyter notebook preprocessing_singer_data.ipynb  # For preprocessing the audio files
jupyter notebook model_singer.ipynb          # For training the audio classification model
jupyter notebook telebot.ipynb          # For running telegram bot

```

## Technologies Used
- Python 3
- TensorFlow/Keras
- NumPy
- Matplotlib
- pydub
- scikit-learn
- pydub
- spleeter
