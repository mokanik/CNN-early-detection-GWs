This folder contains notebooks and data for Project 4 of CAML 2022-2023.

data manipulation.ipynb: 
used to load thousands of files such as 0000001_1_H1.npy, Fourier transform their time series into frequency spectra, and give output as a huge (~7GB) array e.g. X_FT_GData.npy and X_FT_GLabels.npy (G stands for Gaussian noise). X_FT_GData.npy stores an array of shape (number of event IDs, number of channels=3, length of Fourier spectra) and X_FT_GLabels.npy of shape (number of event IDs), where the rows of these arrays correspond to each other. In older versions of data manipulation notebook, train-test split was performed in a customly defined function, but this has been moved to the keras_cnn_jupyterVersion.ipynb. Usual notation is "X_FT_GData_{}.npy".format(level) for level in 0,1,...4.

keras_cnn_jupyterVersion.ipynb:
loads X_FT_GData.npy and X_FT_GLabels.npy, performs sklearn traintest split to split the former into X_train, X_test and latter into y_train, y_test. Defines the CNN and levels. Trains CNN iteratively on levels. However, contrary to initial plans, in practical usage only one level at a time needs to be passed into "levels" list, and levels changed manually. The main output of this notebook is a keras model object that stores the learnt CNN coeffs.

data analysis.ipynb:
loads the model at specified path and the test data at specified path, uses them to calculate performance metrics, choose suitable detection threshold, and draw some graphs.

folder FT_data: if not present, look at cluster: /data/gravwav/dnobile/FT_data where files like X_FT_GData.npy are located (ignore those in the parent directory, they are not the most recent ones)