# Instrument-Classification
## Objective
The goal for this project is to create a neural net classifier that can identify the instrument family of an audio sample no matter if the sample is acoustic, electronic, or synthetic. In modern music, instruments come from many different sources and have infinitely many sound qualities. Sorting through samples or deciding how to use a certain instrument in music production can be difficult if you aren't sure how to define the sound. However, many electronic and synthetic instruments are meant to sound like traditional acoustic instruments. Is it possible to sort unknown instruments into categories?

The NSynth dataset (https://magenta.tensorflow.org/nsynth) is a large-scale audio dataset that can be utilized for such a task. It contains 305,979 musical notes, each with a unique pitch, timbre, and envelope. Each audio sample contains 13 features including:
  * **note**: A unique integer identifier for the note.
  * **note_str**: A unique string identifier for the note.
  * **instrument**: A unique, sequential identifier for the instrument the note was synthesized from.
  * **instrument_str**: A unique string identifier for the instrument this note was synthesized from.
  * **pitch**: The 0-based MIDI pitch in the range [0, 127].
  * **velocity**: The 0-based MIDI velocity in the range [0, 127].
  * **sample_rate**: The samples per second for the audio feature.
  * **audio**: A list of audio samples represented as floating point values in the range [-1,1].
  * **qualities**: 	A binary vector representing which sonic qualities are present in this note.
  * **qualities_str**: A list IDs of which qualities are present in this note selected from the sonic qualities list.
  * **instrument_family**: The index of the instrument family this instrument is a member of.
  * **instrument_family_str**: The ID of the instrument family this instrument is a member of.
  * **instrument_source**: The index of the sonic source for this instrument.
  * **instrument_source_str**: The ID of the sonic source for this instrument.
Using the different features, we plan to classify the *instrument_family* for each test sample. The dataset can be downloaded in both JSON (w/o audio) and TFRecord files. We started with the JSON format for simplicity, but the TFRecord data is more complete containing the audio signals.

## Files
  * __*instrument_classifier_1*__ contains our first attempt using only the source, pitch, and velocity features to classify the audio samples. The JSON version of the dataset does not contain the audio signals themselves (they're contained in separate wav files), so this model only uses minimal features and only reaches about 43% accuracy.
  * __*instrument_classifier_2*__ contains our second attempt that adds in the *qualities* feature. This model is an improvement, but still only reaches about 57% accuracy.
  * __*NSynth_example*__ goes through one example of the TFRecord dataset. It parses through the features and plots the audio sample.
