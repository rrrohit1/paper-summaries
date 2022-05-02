# vision-project

### Why object detection instead of image classification?
1. Ability of identify multiple objects in a frame
2. Localization of object is provided.

### Performance metric
1. Regression: calculating the spatial precision of the boxes. **Intersection over Union (0<=IoU<=1)** area calculates the overlap between ground-truth and the predicted box. A threshold is chosen to eliminate low IoU boxes.
2. Classification: **mean Average Precision(mAP)** is mean of Average Precisions computed over all the classes of the problems which avoids to have extreme specialization is some classses leading to weaker performances in other classes.


