# The Face Synthetics Dataset

Face Synthetics dataset is a collection of diverse synthetic face images with ground truth labels.

Our dataset contains:
- 100,000 images of 512 x 512 pixel resolution
- 70 standard facial landmark annotations
- per-pixel semantic class anotations

It can be used to train machine learning systems for face-related tasks such as landmark localization and face parsing, showing that synthetic data can both match real data in accuracy as well as open up new approaches where manual labelling would be impossible.

The Face Synthetics Dataset is licensed under the license found in EULA.txt

## Downloading the dataset

A sample dataset with 100 images (50MB) can be downloaded directly from [here](https://facesyntheticspubwedata.blob.core.windows.net/iccv-2021/dataset_100.zip)

A sample dataset with 1000 images (500MB) can be downloaded directly from [here](https://facesyntheticspubwedata.blob.core.windows.net/iccv-2021/dataset_1000.zip)

A full dataset of 100,000 images (50GB) can be downloaded from [here](https://facesyntheticspubwedata.blob.core.windows.net/iccv-2021/dataset_100k.zip)

## Dataset layout

The Face Synthetics dataset consists of a collection of face images with corresponding ground truth annotations:

```
├── {subj_id}.png        # Rendered image of a face
├── {subj_id}_seg.png    # Segmentation mask corresponding to the image, encoded as an integer for semantic category
├── {subj_id}_ldmks.txt  # Landmark annotations for 70 facial landmarks (x, y) coordinates for every row
```

Our landmark annotations follow the 68 landmark scheme from [iBUG](https://ibug.doc.ic.ac.uk/resources/300-W/) with additional 2 points for pupil centre. 
Please note that our 2D landmarks are projections of 3D points and do not follow the outline of the face/lips/eyebrows the same way as would be expected from manually annotated landmarks.
They can be through of as X-ray version of 2D landmarks.

Our dataset has the following 19 semantic segmentaiton classes
```
    BACKGROUND = 0
    SKIN = 1
    NOSE = 2
    RIGHT_EYE = 3
    LEFT_EYE = 4
    RIGHT_BROW = 5
    LEFT_BROW = 6
    RIGHT_EAR = 7
    LEFT_EAR = 8
    MOUTH_INTERIOR = 9
    TOP_LIP = 10
    BOTTOM_LIP = 11
    NECK = 12
    HAIR = 13
    BEARD = 14
    CLOTHING = 15
    GLASSES = 16      # Note that opaque lenses are labeled as glasses, while transparent lenses as the class behind them
    HEADWEAR = 17
    FACEWEAR = 18
    IGNORE = 255
```

## Disclaimer

Some of our rendered faces may be close in appearance to the faces of real people.  Such similarity is naturally unintentional, as it would be in a dataset of real images, where some people may appear similar to others unknown to them.


## Generalization to real data

Our dataset can be used to train machine learning models that generalize to real images. For best results, we suggest you follow the methodology described in our paper - **Fake it till you make it: face analysis in the wild using synthetic data alone** (citation below). Especially note the need for 1) data augmentation; 2) use of a translation layer if evaluating on real data benchmarks that contain different types of annotations.

Our dataset strives to be as diverse as possible and can be expected to generalize to a number of environments. However, you may encounter situations where it does not generalize as well. We always recommend that machine learning practitioners test their models on real data that is representative of the target deployment scenario, before deploying the models.


## Citation

If you use the Face Synthetics dataset your research, please cite the following [paper](TODO link to arxiv?):


```
@article{wood2021fakeit
    author  = {Wood, Erroll and Baltrusaitis, Tadas and Hewitt, Charlie and Dziadzio, Sebastian and Cashman, Thomas J. and Shotton, Jamie},
    title   = {Fake it till you make it: Face analysis in the wild using synthetic data alone},
    journal = {ICCV},
    year    = {2021},
}
```
