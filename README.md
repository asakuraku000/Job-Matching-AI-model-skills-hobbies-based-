# Job Matching AI Model

A TensorFlow Lite model for job matching in Flutter apps. Analyzes job descriptions and matches them with user skills.

## Overview

Deep learning model that predicts job categories and calculates match scores between jobs and user skills. Built with CNN-LSTM architecture for mobile deployment.

## Features

- **Job Category Prediction**: Classifies jobs into 20+ categories
- **Match Score Calculation**: Rates job-skill compatibility (0-1)
- **Mobile Optimized**: Exports to TensorFlow Lite for Flutter
- **Offline Capable**: Runs locally in mobile apps

## Installation

```bash
pip install tensorflow numpy pandas scikit-learn joblib
```

## Usage

### 1. Train & Export Model
```python
from job_matching_model import JobMatchingSystem

# Train model
job_matcher = JobMatchingSystem()
job_matcher.train()

# Export to TensorFlow Lite
converter = tf.lite.TFLiteConverter.from_keras_model(job_matcher.model)
tflite_model = converter.convert()

# Save .tflite file
with open('job_matching_model.tflite', 'wb') as f:
    f.write(tflite_model)
```

### 2. Add to Flutter App

Place the exported model in Flutter assets:

```yaml
# pubspec.yaml
flutter:
  assets:
    - assets/models/job_matching_model.tflite
    - assets/models/tokenizer.json
    - assets/models/skill_encoder.json
```

### 3. Flutter Integration

```dart
import 'package:tflite_flutter/tflite_flutter.dart';

class JobMatchingService {
  late Interpreter _interpreter;
  
  Future<void> loadModel() async {
    _interpreter = await Interpreter.fromAsset('assets/models/job_matching_model.tflite');
  }
  
  Map<String, double> predict(String jobDescription, List<String> userSkills) {
    // Implementation for running inference
  }
}
```

## Model Performance

- **Accuracy**: ~85-90%
- **Model Size**: ~2-5MB (TFLite)
- **Inference Time**: <100ms on mobile

## Supported Categories

Software Developer, UI/UX Designer, Teacher, Healthcare Worker, Marketing Specialist, Chef, Veterinarian, Social Worker, Personal Trainer, Construction Manager, Writer, Childcare Provider, Event Coordinator, Landscaper, Travel Guide, Actor, Singer, Game Developer, Sports Coach, Volunteer Coordinator

## Files

- `job_matching_model.py` - Training script
- `job_matching_model.ipynb` - Jupyter notebook
- `job_matching_model.tflite` - Exported mobile model
- `tokenizer.json` - Text preprocessing
- `config.json` - Model configuration

## Contact

**Email**: asakuraku000@gmail.com

