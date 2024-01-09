Automatic Music generator for Piano with LSTM Neural Networks

Music has always been a fascinating form of human expression. How do we come up with musical phrases? Is it just a random selection of notes or is there a pattern to what we make? The ability to generate music using artificial intelligence has opened up new insights in understanding the music making process and exciting possibilities for the future of music composition. In this project, we explore LSTM (Long Short-Term Memory) neural networks and how it can be used to generate music based on MIDI files.

Libraries used:

music21: Python library designed for computer-aided musicology. 
In this project, it is primarily used for parsing MIDI files and working with musical notation elements such as notes, chords, and instruments. The library provides functionality to represent, analyze, and manipulate musical structures.

Glob: Employed for retrieving file paths based on a specified pattern. In this project, it is used to obtain a list of MIDI files from a given directory:

Tqdm: Library for adding progress bars to loops. It provides a visual representation of the progress during tasks that involve iterations. In this project, tqdm is used to display a progress bar while processing MIDI files:

Numpy: A powerful library for numerical operations in Python. In this project, it is used for various array manipulations, including creating NumPy arrays to store musical data:

Random: Used to generate a random index. In this project it is used for selecting a pattern from the testing set during the music generation phase:

 Keras:  A high-level neural networks API that runs on top of other popular deep learning frameworks. In this project, it is used to define, compile, train, and save the LSTM neural network model for music generation.

 sklearn (scikit-learn): is a flexible machine learning library. In this project, it is used to split the dataset into training and testing sets:

Process Steps

1. Data Loading and Preprocessing: 
Load MIDI files containing musical data and extract notes and chords from the piano instrument.

2. Frequency Analysis and Filtering:
Calculate the frequency of each unique musical note and filter out less frequent notes.

3. Note Indexing and Sequence Creation:
Index unique notes and generate new sequences based on the filtered data, creating input-output pairs with a context of 50 notes for LSTM model training.

4. LSTM Model Construction:
Construct a Keras Sequential model with two stacked LSTM layers, incorporating dropout for regularization and a dense layer for output.

5. Model Compilation and Training:
Compile the model using the Adam optimizer and sparse categorical cross-entropy loss. Train the model on a dataset with 80% for training and 20% for testing over 10 epochs.

6. Model Saving and Loading:
Save the trained model as "s2s" for future predictions and load the model when generating new music sequences.

7. Music Generation and MIDI File Creation:
Select a random index from the testing set, retrieve the corresponding data, and use the LSTM model to predict the next 200 musical notes. Transform the generated notes into a music21 stream and create a MIDI file.


Possible Improvements
1) Hyperparameter Tuning: Optimize model hyperparameters such as the number of LSTM layers, units, and dropout rates for improved performance.
2) Bidirectional LSTM: Implement bidirectional LSTM layers to capture longer-term dependencies in the music.
3) Variable-Length Sequences: Explore the use of variable-length sequences to capture nuanced patterns in the music.
