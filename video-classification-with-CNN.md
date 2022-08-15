This is a review of the paper titled `Large-scale Video Classification with Convolutional Neural Networks`.

### Introduction
1. The key enabling factors behind image recogintion
results were techniques for scaling up the networks to tens
of millions of parameters and massive labeled datasets that
can support the learning process.

2. Difficulties with video:
    - there are currently no video
classification benchmarks that match the scale and variety
of existing image datasets because videos are significantly
more difficult to collect, annotate and store.
    -  what temporal connectivity pattern in a CNN architecture is best at taking advantage
of local motion information present in the video?

3. Mitigating large computational power and runtime of the models (2-4x runtime):
    - a `context stream` that learns features
on low-resolution frames
    - a `high-resolution fovea stream`
that only operates on the middle portion of the frame.

### Approach to video classification
1. The standard approach to video classification involves three major stages: 
First, local visual features that describe a region of the video are 
extracted either densely [25] or at a sparse set of interest points [12, 8].
2. Next, the features get combined into a fixed-sized videolevel description.
3. Lastly, a classifier (such as an SVM) is trained on
the resulting ”bag of words” representation to distinguish
among the visual classes of interest.

Convolutional Neural Networks [15] are a biologicallyinspired class of deep learning models that replace all three
stages with a single neural network that is trained end to
end from raw pixel values to classifier outputs.

### Approach by the paper
1. In
this work we treat every video as a bag of short, fixed-sized
clips.
2. we describe three broad connectivity pattern
categories (Early Fusion, Late Fusion and Slow Fusion) below.
3. Afterwards, we describe a multiresolution architecture
for addressing the computational efficiency.

#### Time information fusion in CNNs


#### Runtime
Reducing layers or resolution decreased accuracy

#### Why Fovewa and context streams
this design takes
advantage of the camera bias present in many online videos,
since the object of interest often occupies the center region.

CNN + Normalizing + Pooling (mutliple iteration)

### Learning
Downpour SGD for optimization
minibatches of 32 size

### Augmentation
1. first cropping to center
region, resizing them to 200 × 200 pixels, randomly sampling a 170 × 170 region, and finally randomly flipping the
images horizontally with 50% probability. 
2. we subtract a constant value of 117 from raw pixel values, which
is the approximate value of the mean of all pixels in our
images.

We split the dataset by assigning 70% of the videos to
the training set, 10% to a validation set and 20% to a test
set.

#### Feature extraction
Notably, the fovea stream learns grayscale, high-frequency features while the context stream models lower frequencies and
colors


Our networks seem to learn well despite
significant label noise: the training videos are subject to
incorrect annotations and even the correctly-labeled videos
often contain a large amount of artifacts such as text, effects, cuts, and logos, none of which we attempted to filter
out explicitly.
