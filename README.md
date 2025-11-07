🔭 Project Title

LIGO Gravity Spy Zooniverse Project: Gravitational Wave Image Classification

🧩 Objective

The notebook aims to classify LIGO spectrogram images (from the Gravity Spy Zooniverse Project) into different glitch categories using deep learning. These glitches represent transient noise patterns in LIGO data, and identifying them accurately is essential for improving gravitational wave signal detection.

🧠 Overview of the Workflow
1. Setup and Data Access

The notebook starts by mounting Google Drive and unzipping the dataset (LIGOGravitySpyZooniverseProject.zip) into the working directory.

from google.colab import drive
drive.mount('/content/gdrive')
!unzip /content/gdrive/MyDrive/Dataset/LIGOGravitySpyZooniverseProject.zip

2. Library Imports

Essential libraries are imported for:

Data handling: os, numpy, pandas

Visualization: matplotlib, seaborn

Machine learning: sklearn.metrics

Deep learning: tensorflow.keras (for CNN model creation, training, and evaluation)

3. Directory Setup

Defines paths for the training, validation, and testing image datasets:

train_dir = '/content/train/train'
test_dir = '/content/test/test'
validation_dir = '/content/validation/validation'

4. Data Exploration

Metadata (trainingset_v1d1_metadata.csv) is read using pandas to understand the image labels.

Distribution of classes is visualized with value_counts(), showing how many images exist for each glitch type.

5. Data Preprocessing & Augmentation

Uses ImageDataGenerator to:

Normalize pixel values (rescaling 0–255 to 0–1)

Apply data augmentation (rotation, zoom, flips) to improve generalization

Splits data into training, validation, and testing sets.

6. Model Architecture (CNN)

A Convolutional Neural Network (CNN) is built using Keras Sequential API.
Typical layers include:

Conv2D + MaxPooling2D (for feature extraction)

Flatten + Dense (for classification)

Dropout (to reduce overfitting)

Optimizer used: Adam
Loss function: categorical_crossentropy
Metrics: accuracy

7. Training Configuration

Implements EarlyStopping and ReduceLROnPlateau callbacks to optimize learning and prevent overfitting.

Model trained on the training data and validated on the validation set.

8. Evaluation

Accuracy and loss curves are plotted to visualize model performance over epochs.

The trained model is evaluated on the test set.

A confusion matrix is generated using sklearn.metrics to show classification performance across all glitch categories.

9. Visualization

Displays:

Sample LIGO glitch images from each class.

Training vs. validation accuracy/loss plots.

Confusion matrix heatmap for model evaluation.

📊 Results (Expected Outcomes)

The model classifies LIGO spectrograms into multiple glitch types.

Accuracy varies depending on the balance and diversity of classes.

Visualization helps interpret model strengths and weaknesses.

🧩 Technologies Used

Python

TensorFlow / Keras

Scikit-learn

Matplotlib / Seaborn

Google Colab

🧠 Conclusion

This notebook demonstrates how deep learning can be effectively applied to astrophysical data analysis — specifically, to classify noise patterns in LIGO’s gravitational wave data. By automating the identification of glitches, such models contribute to improving the accuracy of gravitational wave detection pipelines.
