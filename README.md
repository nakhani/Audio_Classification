# **Speaker & Singer Classification Project 🎙️🤖**

This repository contains **multiple subprojects** focused on **audio processing, classification, and Telegram bot integration**. Below is a brief overview of each project.

---

## **1️⃣ Make Audio Dataset (using PyDub) 🎼**
- Extract **voice messages from Telegram**
- Merge **audio files of the same person**
- Remove **silence segments**
- Convert **audio files to WAV format**
- Split voices into **1-second chunks**
- Upload dataset to **Google Drive** for easy sharing

## **2️⃣ Train a Speaker Classification Model (using TensorFlow) 🏆**
- Load dataset with:
  ```python
  tf.keras.utils.audio_dataset_from_directory
  ```
- Build a **Conv1D-based neural network**
- Train the model and **report validation accuracy**
🔹 **Telegram Bot**: Classifies **voice messages** to recognize speakers

## **3️⃣ Persian Singer Identification (using Spleeter) 🇮🇷🎤**

- Select **5 Persian singers** (Mohsen Chavoshi, Mohsen Yeganeh, Ebi, etc.)
- **Extract vocals** from songs using **Spleeter**
- Create a structured **dataset for training**
- Train a deep learning model to **identify singers**
🔹 **Telegram Bot**: Classifies **voice messages** to recognize singer


## **4️⃣ Telegram Bot Integration 🤖**

- Build a **Telegram bot** to handle user voice submissions

   <img src="Accuracy.png" width = "300">
   <img src="Accuracy.png" width = "300">
   
- Process received voice messages automatically
- Run predictions using **trained models**
- Display classification results in **real-time**
- Supports both **friend recognition** and **singer identification**
- You can Download weights here:
  - **📥 Download persian friend classification model**: [Download Here](https://drive.google.com/file/d/1A4raAU0s7rcTN7wEHYDtFxvTYsuFIef3/view?usp=sharing) 
  - **📥 Download persian singer classification model**: [Download Here](https://drive.google.com/file/d/1CgTtGdwv3i2CSXwIXP9No_dLj5-1pd39/view?usp=sharing) 

---

## **🛠 Running Each Project**
Each project is stored in a separate directory with its own README file. 👉 To run a specific project, open its directory and follow the step-by-step instructions in its README.