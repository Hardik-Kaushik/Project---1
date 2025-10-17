# Data

All BraTS multimodal scans are available as NIfTI files (.nii.gz) and describe a) native (T1) and b) post-contrast T1-weighted (T1Gd), c) T2-weighted (T2), and d) T2 Fluid Attenuated Inversion Recovery (T2-FLAIR) volumes.

Annotations comprise the GD-enhancing tumor (ET — label 4), the peritumoral edema (ED — label 2), and the necrotic and non-enhancing tumor core (NCR/NET — label 1).
You can look at the 3d data projection [here](https://www.kaggle.com/polomarco/brats20logs/) or [here](https://www.youtube.com/watch?v=0nliIOj2WVQ).

# Formulation of the problem:
+ 1. Each pixel must be labeled “1” if it is part of one of the classes (NCR/NET — label 1, ED — label 2, ET — label 4), and “0” if not.
+ 2. Make a prediction of age and survival days for each unique identifier in the data.

# Solution
+ 1. For automatic segmentation we will use Unet3d
+ 2. To predict the age and number of days of survival: first, we will train the auto-encoder to scale the space from 4 * 240 * 240 * 150 to 512, and then extract the statistical values, ​​and hidden representations for each identifier in the data encoded by the pre-trained auto-encoder and based on this tabular data we will train SVR.
