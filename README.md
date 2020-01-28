# P3D
Plant 3D (P3D): A plant phenotyping toolkit for 3D point clouds

![Test](P3D_figure_V3.JPG)

<h2> What is P3D?</h2>
  
Plant 3D (P3D) automatically extracts common phenotyping features of interest from high-resolution 3D scans of plant architectures. 
P3D is open-source and is bundled with a stand-alone Windows application. P3D is written in C++ using OpenGL, QT, TensorFlow, and the point cloud library (PCL). 
P3D can visualize and process data imported as a 3D point cloud (<TT>pcd</TT> or <TT>txt</TT> formats) or a mesh (<TT>obj</TT> format). 

<h3>The tool focuses on four phenotyping tasks</h3> 
<OL>
  <li>Lamina VS. stem classification</li>
  <li>Lamina counting and segmentation</li>
  <li>Stem skeletonization</li>
  <li>Whole leaf labeling</li>
</OL>

<!-- Classification ------------------------------------------------------------------------------------------------------->

<h3> <img src="./imgs/classify_border.png"> Classification </h3>

Points are classified by a trained deep learning model.
The model uses binary classification and separates lamina and stem points.
Prior training each 3D point was embedded into 33D FPFH (Fast Point Feature Historgram) space using [Point Cloud Library](http://www.pointclouds.org/).
The enference begins by taking input point cloud and computes FPFH for each point, result is pumped through trained deep learning model.
P3D comes with a few pretrained models. Models can be found in TF_Models folder with __".pb"__ tensorflow file extension.
To use a model, click on _classify_ button (button icon at the top) on the left menu, controls panel on the lower right should appear. 
In the controls panel click __Browse__ button to provide a path to __".pb"__ file and then click __Run Classification__.
For details on why FPFH was selected, what parameters, data were used for training please refer to our publication (See link below).

<!-- Segmentation -------------------------------------------------------------------------------------------------------->

<h3> <img src="./imgs/lamina_segement_border.png"> Lamina counting and segmentation</h3>

Similarly to classification clicking on segmentaion icon on the left panel will bring lamina segmentation controls panel on the lower right. Menu provides many options to do lamina segmentation. The method is an enhanced version of conditional region growing.
To use lamina segmentaion on user's files that already been classified else where and only contain lamina points a particular naming convetion must be followed (Described below). 

<!-- Skeletonization -------------------------------------------------------------------------------------------------------->

<h3> <img src="./imgs/roots.png"> Stem skeletonization</h3>

Our approach to stem skeletanization builds upon [PypeTree framework](https://www.mdpi.com/1424-8220/14/3/4271).
We improved on speed and accuracy. Improvements as well as detailed table of comparisons is presented in our publication (below). Stem file naming convetion need to be followed to run this methods as well. (below)

<!-- Leaf labeling -------------------------------------------------------------------------------------------------------->

<h3> <img src="./imgs/leaf_labeling.png"> Whole leaf labeling</h3>

Leaf labeling task consolidates the information gathered from lamina segmentation and skeletanization to produce a point cloud where
each point is labeled as one of the following: main stem, leaf in biological sense or cotyledon.
Currenlty this task in only available for tomato plants. 
To run this method both stem and lamina files need to named according to the convention (below) when imported to P3D.
For more details refer to the publication.

<!-- Conventions -------------------------------------------------------------------------------------------------------->

<h3> Naming conventions </h3>
For the tasks to function properly a particular naming conventions need to be followed. 
All task except for classification expect this format.

```
plant_name_l.pcd or plant_name_l.txt  // "_l" stands for lamina points
plant_name_s.pcd or plant_name_s.txt  // "_s" stands for stem points
```

Classification if ran on any file will produce two sets of points and name them according to the convetions automatically.



<h3> How to run:</h3>
  
  
<h3> Source:</h3>
  
  
<h2> Models</h2>

TF_Models folder contains deep learning model/s trained on our dataset on extracted FPFH features. 
To use the any of the models download a model you want and supply a path to it during classification. 
Prior inference P3D will compute FPHF features for every point.
Parameters for FPFH computation are set to the same values as during training.
  
<h2> Motivation</h2>

Developing methods to accurately process large volumes of 3D point clouds remains challenging for many 3D plant phenotyping applications. Here, we describe a tool that addresses four core phenotyping tasks: classification of cloud points into lamina and stem points; graph skeletonization of the stem points; segmentation of lamina points into individual lamina; and whole leaf labeling composed of individual lamina. These four tasks are critical for numerous downstream phenotyping goals, such as quantifying plant biomass, performing morphological analyses of plant shapes, and uncovering genotype to phenotype relationships. The P3D tool provides an intuitive graphical user interface, a fast 3D rendering engine for visualizing plants with millions of cloud points, and several graph-theoretic and machine learning algorithms for 3D plant architecture analyses. As 3D point clouds become a standard data type for collecting plant architecture data in the lab and in the field, the P3D tool can help accelerate next-generation plant phenotyping.

<h2> Publication </h2>

For many details not mentined here please refer to our _Plant Physiology_ publication:

[_Machine Learning Approaches to Improve Three Basic Plant Phenotyping Tasks Using Three-Dimensional Point Clouds_](http://www.plantphysiol.org/content/181/4/1425)
