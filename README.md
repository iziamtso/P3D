# P3D
Plant 3D (P3D): A plant phenotyping toolkit for 3D point clouds

![Test](P3D_figure_V3.JPG)

<h2> What is P3D?</h2>
  
Plant 3D (P3D) automatically extracts common phenotyping features of interest from high-resolution 3D scans of plant architectures. 
P3D is open-source and is bundled with a stand-alone Windows application. P3D is written in C++ using OpenGL, QT, TensorFlow, and the point cloud library (PCL). 
P3D can visualize and process data imported as a 3D point cloud (<TT>pcd</TT> or <TT>txt</TT> formats) or a mesh (<TT>obj</TT> format). 

<h3>The tool focuses on four phenotyping tasks</h3> 
<OL>
  <li>Lamina vs stem classification</li>
  <li>Lamina counting and segmentation</li>
  <li>Stem skeletonization</li>
  <li>Whole leaf labeling</li>
</OL>
The algorithms developed for these tasks are novel and were recently shown to improve accuracy and/or run-time, compared to existing methods, on a large dataset of 3D plant architectures~\citep{Ziamtsov2019}. 

<h3> How to run:</h3>
  
  
<h3> Source:</h3>
  
  
<h3> Models</h3>
Models folder contains deep learning model/s trained on our dataset on extracted FPFH features. 
To use the any of the models download a model you want and supply a path to it during classification. 
Prior inference P3D will compute FPHF features for every point, the default is set with the same parameters as trained inference networks.
  
  
<h3> Motivation</h3>
Developing methods to accurately process large volumes of 3D point clouds remains challenging for many 3D plant phenotyping applications. Here, we describe a tool that addresses four core phenotyping tasks: classification of cloud points into lamina and stem points; graph skeletonization of the stem points; segmentation of lamina points into individual lamina; and whole leaf labeling composed of individual lamina. These four tasks are critical for numerous downstream phenotyping goals, such as quantifying plant biomass, performing morphological analyses of plant shapes, and uncovering genotype to phenotype relationships. The P3D tool provides an intuitive graphical user interface, a fast 3D rendering engine for visualizing plants with millions of cloud points, and several graph-theoretic and machine learning algorithms for 3D plant architecture analyses. As 3D point clouds become a standard data type for collecting plant architecture data in the lab and in the field, the P3D tool can help accelerate next-generation plant phenotyping.
