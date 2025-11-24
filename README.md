<b>CZII - CryoET Object Identification</b>

Advancing 3D Protein Complex Annotation with Deep Learning
***
<b>📌 Overview</b>

Cryo-electron tomography (Cryo-ET) provides high-resolution 3D visualization of cellular environments, capturing protein complexes in their native molecular context. However, automated particle detection remains challenging due to:

<b>1</b> High noise levels

<b>2</b> Low contrast

<b>3</b> Missing-wedge artifacts

<b>4</b> Dense and crowded molecular environments

This project introduces a YOLO-based deep learning pipeline for detecting and localizing protein complexes in Cryo-ET tomograms. Using synthetic Zarr-based datasets, the workflow integrates preprocessing, multi-slice feature extraction, and k-d tree–based refinement to improve localization accuracy.
***
<b>📂 Dataset Description</b>

The dataset includes 3D tomograms with ground-truth particle center annotations for five scored classes.

<b>Scored Particle Types</b>

<b> 1.Easy</b>

<i>   Apo-ferritin</i>

<i>   Ribosome</i>

<i>   Virus-like particle</i>

<b> 2.Hard </b>

<i>   β-galactosidase</i>

<i>   Thyroglobulin</i>

<b>3.Not Scored</b>

<i>   β-amylase<i>
***
<b>📥 Download Dataset</b>

Kaggle Competition:
https:/**/www.kaggle.com/competitions/czii-cryo-et-object-identification/data
***
<b>📁 Dataset Structure</b>


<img width="379" height="175" alt="image" src="https://github.com/user-attachments/assets/f2a77626-9481-4382-9e58-6c8bae934f0e" />


***
<b>⚙️ Installation</b>
Download YOLO (Ultralytics) for Offline Use
<pre style="background:#272822;color:#f8f8f2;padding:12px;border-radius:6px;overflow:auto;"> <code>!pip download -d ./packages ultralytics !tar cfvz archive.tar.gz ./packages</code></pre>
Install YOLO Offline
<pre style="background:#272822;color:#f8f8f2;padding:12px;border-radius:6px;overflow:auto;"> <code>!tar xfvz /kaggle/input/ultralytics-for-offline-install/archive.tar.gz !pip install --no-index --find-links=./packages ultralytics !rm -rf ./packages</code></pre>
Install Required Dependencies
<pre style="background:#272822;color:#f8f8f2;padding:12px;border-radius:6px;overflow:auto;"> <code>!cp -r '/kaggle/input/hengck-czii-cryo-et-01/wheel_file' '/kaggle/working/'</code></pre>
Install asciitree and zarr
<pre style="background:#272822;color:#f8f8f2;padding:12px;border-radius:6px;overflow:auto;"> <code>!pip install /kaggle/working/wheel_file/asciitree-0.3.3/asciitree-0.3.3.whl !pip install --no-index --find-links=/kaggle/working/wheel_file zarr</code></pre>
***
<b>🏗️ Model Details</b>

<b>Architecture:</b> YOLO-based 2.5D/3D-aware detector

<b>Training Data:</b> Synthetic Cryo-ET dataset (best_synthetic.pt)

<b>Evaluation Metric:</b> F-β score (β = 4), recall-weighted

<b>Post-Processing:</b> k-d tree refinement, confidence filtering, NMS
***
<b>🔄 Preprocessing & Post-processing</b>

<b>Preprocessing</b>

<i>Multi-slice feature extraction</i>

<i>Intensity normalization</i>

<i>Noise reduction</i>

<i>Spatial consistency enhancement</i>

<b>Post-processing</b>

<i>k-d tree–based spatial refinement</i>

<i>Non-maximum suppression</i>

<i>Confidence thresholding</i>
***
<b>📊 Results</b>

<i>High-recall protein complex detection in noisy tomograms</i>

<i>Stable localization across synthetic volumes</i>

<i>k-d tree refinement significantly improves spatial accuracy</i>
<b>Submission format</b>
![image](https://github.com/user-attachments/assets/f33fad58-7d2c-4a6f-9361-39bfa7ce309f)
***
##### Kaggle Scores (private and public)

![image](https://github.com/user-attachments/assets/e4d7eb32-bff0-4aca-b640-5c855e3b772b)
***


