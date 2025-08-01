This project focuses on building a binary image classification system using deep learning to automatically detect forest fires from images. The goal is to differentiate between two classes:

Fire

No Fire

📁 Dataset
Source: Local directory containing two subfolders – one for each class (fire, nofire).

Structure:

Each folder contains .jpg, .jpeg, or .png images.

A Pandas DataFrame is used to store:

filepath: full image path.

label: category name.

class_id: numerical representation (fire = 0, nofire = 1).

🧹 Data Preprocessing
Images are resized to 150x150 pixels.

Normalized and loaded using image generators or a preprocessing pipeline (assumed).

Data is split into training and validation sets.

🧠 Model Architecture
A Sequential CNN model built using TensorFlow/Keras:

python
Copy
Edit
model = keras.Sequential([
    keras.layers.Conv2D(32, (3, 3), activation='relu', input_shape=(150, 150, 3)),
    keras.layers.MaxPool2D(2, 2),

    keras.layers.Conv2D(64, (3, 3), activation='relu'),
    keras.layers.MaxPool2D(2, 2),

    keras.layers.Conv2D(128, (3, 3), activation='relu'),
    keras.layers.MaxPool2D(2, 2),

    keras.layers.Conv2D(128, (3, 3), activation='relu'),
    keras.layers.MaxPool2D(2, 2),

    keras.layers.Flatten(),
    keras.layers.Dense(512, activation='relu'),
    keras.layers.Dense(1, activation='sigmoid')  # Binary output
])
⚙️ Compilation
python
Copy
Edit
model.compile(
    optimizer='adam',
    loss='binary_crossentropy',
    metrics=['accuracy']
)
🏋️‍♀️ Training
Trained for 7 epochs on the training dataset.

Validation accuracy tracked using:

python
Copy
Edit
model.fit(train_dataset, epochs=7, validation_data=test_dataset)
📈 Evaluation (Expected)
Though evaluation plots weren't previewed yet, it is likely that training and validation:

Accuracy curves and loss curves were plotted using matplotlib.

✅ Outcome
The model learns to classify forest fire and non-fire images with binary classification.

A practical solution for early forest fire detection using AI.










