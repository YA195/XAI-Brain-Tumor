# Brain Tumor Segmentation & Explainability Project

## Project Overview  
This repository implements and compares three convolutional models for brain tumor segmentation on the BraTS18 dataset, and applies XAI techniques to interpret their predictions:

1. **Standard U-Net**  
2. **Attention U-Net**  
3. **Patch-based MLP**

For each model, we train on preprocessed MRI slices, evaluate segmentation performance, and visualize how the models make decisions using Grad-CAM, Saliency Maps, and Permutation Importance.

---

## Repository Structure

```
├── data/
│   └── BraTs18.zip              # Raw BraTS18 archive
├── notebooks/
│   ├── Model_1Jilan_Ismail.ipynb   # Standard U-Net experiment
│   ├── Model2_JilanIsmail.ipynb    # Attention U-Net + Grad-CAM & Saliency
│   └── Model3_JilanIsmail.ipynb    # Patch-MLP + Grad-CAM & Permutation Importance
├── requirements.txt             # Python dependencies
└── README.md                    # This file
```

---

## Requirements

- Python 3.8+  
- TensorFlow 2.x  
- scikit-image == 0.19.3  
- NumPy, pandas, matplotlib  
- (Optional for XAI) `tf-explain` or custom Grad-CAM scripts  

Install all dependencies via:

```bash
pip install -r requirements.txt
```

---

## Dataset & Preprocessing

1. **Download** the BraTS18 dataset and place `BraTs18.zip` in `data/`.  
2. **Unzip**:
   ```bash
   unzip data/BraTs18.zip -d data/BraTs18/
   ```
3. **Preprocessing** steps (in each notebook):
   - Load NIfTI MRI modalities (e.g., T1, T2, FLAIR).
   - Normalize intensities to [0,1].
   - Resize slices to 112×112.
   - Extract 2D slices and corresponding binary masks.
   - Train/test split (80/20).

---

## Usage

Open any notebook under `notebooks/` and run all cells in order. Each notebook is self-contained:

1. **Environment setup**  
2. **Data loading & preprocessing**  
3. **EDA** (distribution of tumor vs. non-tumor pixels)  
4. **Model definition**  
5. **Training loop** (with callbacks and checkpoints)  
6. **Evaluation** (Dice score, IoU, pixel accuracy)  
7. **XAI analysis** (Grad-CAM, Saliency, Permutation Importance)

---

## Results Summary

| Model               | Dice Score (val) | IoU (val) | Inference Speed |  
|---------------------|------------------|-----------|-----------------|  
| Standard U-Net      | 0.82             | 0.75      | ~25 ms/slice    |  
| Attention U-Net     | 0.85             | 0.78      | ~30 ms/slice    |  
| Patch-based MLP     | 0.77             | 0.70      | ~15 ms/slice    |  

---

## Explainability

- **Grad-CAM** highlights regions most influential to each class.  
- **Saliency Maps** show pixelwise gradient sensitivity.  
- **Permutation Importance** overlays how shuffling input patches changes output confidence.

---

## Contributing

Feel free to:

- Add more XAI methods (e.g., Integrated Gradients).  
- Experiment with different patch sizes or deeper U-Nets.  
- Test on newer BraTS editions.

---

## License

This project is released under the MIT License.
