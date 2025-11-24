CZII - CryoET Object Identification
Advancing 3D Protein Complex Annotation with Deep Learning
📌 Overview

Cryo-electron tomography (Cryo-ET) enables high-resolution 3D visualization of cellular environments, capturing protein complexes in their native, crowded states. Despite its power, automated detection remains difficult due to:

High noise levels

Low contrast

Missing-wedge artifacts

Dense molecular environments

This project presents a YOLO-based deep learning pipeline for detecting and localizing protein complexes in Cryo-ET tomograms. Using synthetic tomograms in Zarr format, the workflow applies advanced preprocessing, multi-slice feature extraction, and k-d tree–based refinement to improve localization accuracy.

📂 Dataset Description

The dataset consists of 3D tomograms and particle-center annotations for five scored classes.

Scored Particle Types

Easy

Apo-ferritin

Ribosome

Virus-like particle

Hard

β-galactosidase

Thyroglobulin

Not scored

β-amylase

Download Dataset

Kaggle Competition (official data):
https://www.kaggle.com/competitions/czii-cryo-et-object-identification/data

📁 Dataset Structure
train/
 ├── static/ExperimentRuns/{experiment}/VoxelSpacing10.000/
 │      └── denoised.zarr/
 └── overlay/ExperimentRuns/{experiment}/Picks/
        └── {particle_type}.json

test/
 └── static/ExperimentRuns/{experiment}/VoxelSpacing10.000/
        └── denoised.zarr/

⚙️ Installation
Download YOLO (Ultralytics) for Offline Use
<code> !pip download -d ./packages ultralytics !tar cfvz archive.tar.gz ./packages </code>
Install YOLO Offline
<code> !tar xfvz /kaggle/input/ultralytics-for-offline-install/archive.tar.gz !pip install --no-index --find-links=./packages ultralytics !rm -rf ./packages </code>
Install Required Dependencies
<code> !cp -r '/kaggle/input/hengck-czii-cryo-et-01/wheel_file' '/kaggle/working/' </code>

Install asciitree and zarr from wheels:
<code>
!pip install /kaggle/working/wheel_file/asciitree-0.3.3/asciitree-0.3.3.whl
!pip install --no-index --find-links=/kaggle/working/wheel_file zarr
</code>

🏗️ Model Details

Architecture: YOLO-based 2.5D/3D-aware detection

Training Data: Synthetic Cryo-ET dataset (best_synthetic.pt)

Evaluation Metric: Weighted F-β score (β = 4) prioritizing recall

Post-Processing: k-d tree refinement, confidence filtering, NMS

🔄 Preprocessing & Post-processing
Preprocessing

Multi-slice extraction

Intensity normalization

Noise reduction

Spatial consistency enhancement

Post-processing

k-d tree–based spatial refinement

Non-maximum suppression (NMS)

Confidence thresholding

📊 Results

High-recall detection of protein complexes in noisy Cryo-ET volumes

Robust localization across synthetic tomograms

k-d tree refinement significantly improved spatial accuracy

📁 Submission Format & Kaggle Scores

(Insert your images, tables, or screenshots here)

🚀 Future Work

Fine-tuning on real Cryo-ET datasets

Improved hyperparameter optimization

More advanced spatial post-processing

Ensemble architectures

Expanded synthetic data generation
