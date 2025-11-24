CZII - CryoET Object Identification

Advancing 3D Protein Complex Annotation with Deep Learning

📌 Overview

Cryo-electron tomography (Cryo-ET) provides high-resolution 3D visualization of cellular environments, capturing protein complexes in their native molecular context. However, automated particle detection remains challenging due to:

High noise levels

Low contrast

Missing-wedge artifacts

Dense and crowded molecular environments

This project introduces a YOLO-based deep learning pipeline for detecting and localizing protein complexes in Cryo-ET tomograms. Using synthetic Zarr-based datasets, the workflow integrates preprocessing, multi-slice feature extraction, and k-d tree–based refinement to improve localization accuracy.

📂 Dataset Description

The dataset includes 3D tomograms with ground-truth particle center annotations for five scored classes.

Scored Particle Types

Easy

Apo-ferritin

Ribosome

Virus-like particle

Hard

β-galactosidase

Thyroglobulin

Not Scored

β-amylase

📥 Download Dataset

Kaggle Competition:
https:/**/www.kaggle.com/competitions/czii-cryo-et-object-identification/data

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
<pre style="background:#272822;color:#f8f8f2;padding:12px;border-radius:6px;overflow:auto;"> <code>!pip download -d ./packages ultralytics !tar cfvz archive.tar.gz ./packages</code></pre>
Install YOLO Offline
<pre style="background:#272822;color:#f8f8f2;padding:12px;border-radius:6px;overflow:auto;"> <code>!tar xfvz /kaggle/input/ultralytics-for-offline-install/archive.tar.gz !pip install --no-index --find-links=./packages ultralytics !rm -rf ./packages</code></pre>
Install Required Dependencies
<pre style="background:#272822;color:#f8f8f2;padding:12px;border-radius:6px;overflow:auto;"> <code>!cp -r '/kaggle/input/hengck-czii-cryo-et-01/wheel_file' '/kaggle/working/'</code></pre>
Install asciitree and zarr
<pre style="background:#272822;color:#f8f8f2;padding:12px;border-radius:6px;overflow:auto;"> <code>!pip install /kaggle/working/wheel_file/asciitree-0.3.3/asciitree-0.3.3.whl !pip install --no-index --find-links=/kaggle/working/wheel_file zarr</code></pre>
🏗️ Model Details

Architecture: YOLO-based 2.5D/3D-aware detector

Training Data: Synthetic Cryo-ET dataset (best_synthetic.pt)

Evaluation Metric: F-β score (β = 4), recall-weighted

Post-Processing: k-d tree refinement, confidence filtering, NMS

🔄 Preprocessing & Post-processing
Preprocessing

Multi-slice feature extraction

Intensity normalization

Noise reduction

Spatial consistency enhancement

Post-processing

k-d tree–based spatial refinement

Non-maximum suppression

Confidence thresholding

📊 Results

High-recall protein complex detection in noisy tomograms

Stable localization across synthetic volumes

k-d tree refinement significantly improves spatial accuracy
