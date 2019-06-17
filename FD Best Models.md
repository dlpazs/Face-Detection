# ArcFace

They try to find the best loss function in face recognition and find that the Additive Angular Margin Loss (ArcFace) is the best at 
enhancing the discriminative power of face recognition. They use a Deep CNN (DCNN) to embed a face and map the face (after normalizing for the pose) 
into a feature that has a small intra-class and large inter-class geodesic distance. The two main approaches for DCNN in face recognition (FR) 
is to use multi-class classification to separate identities (using softmax classifier) or by learning directly an embedding of a face. 
Both methods work. Variants on the softmax loss include: centre loss (Euclidean distance between each feature vector and its class centre, 
intra-class compactness and inter-class dispersion is done via joint penalisation of the softmax loss). They employ Additive Angular Margin Loss 
to improve discriminative power and stabilise training. The dot product of the DCNN feature and last fully connected layer is equal to the 
cosine distance after feature and weight normalisation.

- To best of our knowledge, we are the first to employ
ethnicity-specific annotators for large-scale face image 
annotations, as the boundary cases (e.g. hard samples and
noisy samples) are very hard to distinguish if the annotator
is not familiar with the identity.

- Dataset: 

|Datasets|#Identity|#Image/Video|
--------------------------------
|CASIA [43] 10K |0.5M|
|VGGFace2 [6] 9.1K |3.3M| ****
|MS1MV2 85K |5.8M|
|MS1M-DeepGlint [2]| 87K |3.9M|
|Asian-DeepGlint [2]| 94 K |2.83M|
|LFW [13]| 5,749 |13,233|
|CFP-FP [30]| 500 |7,000|
|AgeDB-30 [22]| 568 |16,488|
|CPLFW [48]| 5,749 |11,652|
|CALFW [49]| 5,749 |12,174|
|YTF [40]| 1,595 |3,425|
|MegaFace [15]| 530 (P) |1M (G)|
|IJB-B [39]| 1,845 |76.8K|
|IJB-C [21]| 3,531 |148.8K|
|Trillion-Pairs [2]| 5,749 (P) |1.58M (G)|
|iQIYI-VID [20]|4,934| 172,835|

[alt text](https://www.groundai.com/media/arxiv_projects/154532/fig/arcFace.png.750x0_q75_crop.png)

Additional Reading:

- https://www.groundai.com/project/arcface-additive-angular-margin-loss-for-deep-face-recognition/


# RetinaFace

Based on a single-stage design, we propose a novel
pixel-wise face localisation method named RetinaFace, which employs a multi-task learning strategy
to simultaneously predict face score, face box, five facial landmarks, and 3D position and correspondence
of each facial pixel.

On the IJB-C dataset, RetinaFace helps to improve ArcFace’s [11] verification accuracy (with TAR equal to
89.59% when FAR=1e-6). This indicates that better
face localisation can significantly improve face recognition.

By employing light-weight backbone networks, RetinaFace can run real-time on a single CPU core for a
VGA-resolution image.

(1) We manually annotate five facial landmarks on the WIDER FACE dataset and observe significant improvement in hard face detection 
with the assistance of this extra supervision signal.
(2) We further add a self-supervised mesh decoder branch for predicting a pixel-wise 3D shape face information in parallel with the 
existing supervised branches.
(3) On the WIDER FACE hard test set, RetinaFace outperforms the state of the art average precision (AP) by 1.1% (achieving AP equal to 91.4%).
(4) On the IJB-C test set, **RetinaFace enables state of the art methods (ArcFace) to improve their results in face 
verification (TAR=89.59% for FAR=1e-6).**
(5) By employing light-weight backbone networks, RetinaFace can run real-time on a single CPU core for a VGA-resolution image
5 facial landmarks 

- Dataset: WIDER FACE

# VGGFace2: A dataset for recognising faces across pose and age

- 3.31 million images, 9131 subjects, 362 images for each subject.
- Variations in pose, age, illumination, ethnicity and profession

The VGGFace2 dataset contains 3.31 million images from
9131 celebrities spanning a wide range of ethnicities, e.g.
it includes more Chinese and Indian faces than VGGFace
(though, the ethnic balance is still limited by the distribution
of celebrities and public figures), and professions (e.g.
politicians and athletes).


# WIDER FACE: A Face detection Benchmark

We show that there is a gap between current face
detection performance and the real world requirements. To
facilitate future face detection research, we introduce the
WIDER FACE dataset, which is 10 times larger than existing datasets. The dataset contains rich annotations, 
including occlusions, poses, event categories, and face bounding
boxes. Faces in the proposed dataset are extremely challenging due to large variations in scale, pose and occlusion.

- 32,203 images 393,703 faces with high degree of variability in scale, pose and occlusion
- The detections are ranked based on Easy, Medium and Hard 


# FaceNet

FaceNet directly learns a mapping from face images to a compact Euclidean space where distances correspond to face similarity. 
Squared L2 distances in embedding space correspond to face similarity (faces of the same person have small distances and faces of 
distinct people have large distances). Once this embedding is established the task of face verification becomes thresholding the 
distance between two embeddings – recognition becomes a k-NN classification problem. They train with triplet images with 2 positives 
and 1 negative and they train the loss to separate the positive pair from the negative by a distance margin. The network consists of 
batches as input a DCNN then L2 normalization 


# SUMMARY OF ETHNIC BIAS AVOIDANCE:

RetinaFace is a strong Face Landmark/Localisation/Bounding Box Regressor/Detector and can run in real-time on a single CPU core. 
The dataset is trained on the Hard subset of the WIDER FACE dataset so will exhibit the biases present therein. WIDER FACE is 
designed to be a really challenging Face Detection benchmark and there is no bias avoidance measure. ArFace is trained on VGGFace2 
which contains ethnicity based labels (but biased towards celebrities/public figures/professions). 
