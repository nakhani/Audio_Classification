# **Speaker & Singer Classification Project 🎙️🤖**

This repository contains **multiple subprojects** focused on **audio processing, classification, and Telegram bot integration**. Below is a brief overview of each project.

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
