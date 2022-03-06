# Create-Image-Dataset-using-Data-Augmentation-using-Keras-Deep-Learning-Data-Science
# Data pre-processing and data augmentation
In order to make the most of our few training examples, we will "augment" them via a number of random transformations, so that our model would never see twice the exact same picture. This helps prevent overfitting and helps the model generalize better.

In Keras this can be done via the keras.preprocessing.image.ImageDataGenerator class. This class allows you to:

1. configure random transformations and normalization operations to be done on your image data during training
2. instantiate generators of augmented image batches (and their labels) via .flow(data, labels) or .flow_from_directory(directory). These generators can then be used with the Keras model methods that accept data generators as inputs, fit_generator, evaluate_generator and predict_generator.

# These are just a few of the options available (for more, see the documentation). Let's quickly go over what we just wrote:

1. rotation_range is a value in degrees (0-180), a range within which to randomly rotate pictures
2. width_shift and height_shift are ranges (as a fraction of total width or height) within which to randomly translate pictures vertically or horizontally
3. rescale is a value by which we will multiply the data before any other processing. Our original images consist in RGB coefficients in the 0-255, but such values would be too high for our models to process (given a typical learning rate), so we target values between 0 and 1 instead by scaling with a 1/255. factor.
4. shear_range is for randomly applying shearing transformations
5. zoom_range is for randomly zooming inside pictures
6. horizontal_flip is for randomly flipping half of the images horizontally --relevant when there are no assumptions of horizontal assymetry (e.g. real-world pictures).
7. fill_mode is the strategy used for filling in newly created pixels, which can appear after a rotation or a width/height shift.
