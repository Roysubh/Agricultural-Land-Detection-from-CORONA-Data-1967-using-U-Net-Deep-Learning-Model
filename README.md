🛰️ Agricultural Land Detection from CORONA Data (1967) using U-Net Deep Learning Model

This project demonstrates the use of a U-Net deep learning model to extract agricultural land from historic CORONA Data (1967) with ~2.5 m resolution. By leveraging modern AI techniques on archival grayscale reconnaissance data, the project enables:
  📍 Accurate cropland detection from 1960s imagery
  🕰️ Retrospective land use mapping
  🌾 Monitoring long-term agricultural changes
  
🧾 Project Overview:
| Parameter         | Description                                          |
| ----------------- | ---------------------------------------------------- |
| **Year**          | 1967                                                 |
| **Satellite**     | CORONA (Grayscale imagery)                           |
| **Resolution**    | \~2.5 meters                                         |
| **Model**         | U-Net (Semantic Segmentation)                        |
| **Patch Size**    | 128 × 128 pixels                                     |
| **Stride**        | 64 (50% overlap)                                     |
| **Output**        | Binary segmentation mask (GeoTIFF) + Shapefile (SHP) |
| **Loss Function** | BCEWithLogitsLoss + Dice Loss                        |
| **Metrics**       | IoU, F1-Score, Precision, Recall                     |

⚙️ Dependencies:
  Install required packages via pip or conda:
    pip install torch torchvision numpy rasterio shapely fiona matplotlib tqdm

🚀 Workflow:
  🔧 Training:
      Input: Grayscale CORONA image patches (128×128)
      Patch extraction: PATCH_SIZE = 128, STRIDE = 64
      Labels: Binary mask (1 = agriculture, 0 = background)
      Model: U-Net with encoder-decoder architecture
      Loss Function: BCEWithLogitsLoss + Dice Loss
    
  🔧 Hyperparameters:
      BATCH_SIZE = 8
      NUM_EPOCHS = 500
      LEARNING_RATE = 1e-4

  🧪 Inference:
       The full image is split into overlapping patches using a sliding window.
       Patches are predicted individually and merged to reconstruct the full binary mask.

  ✅ Best Model Saved at Epoch 500 with
       IoU: 0.9746
       F1-Score, Precision, Recall: High and consistent across test data

  Final outputs:
    GeoTIFF: Binary segmentation mask of agriculture
    SHP: Extracted agriculture polygons as vector shapefile

🧠 U-Net Model Overview
      Input: 128×128 grayscale image
      Output: Per-pixel classification (0 or 1)
      Architecture: U-Net with skip connections
      Training Data: Manually labeled agricultural land from CORONA
      
  Evaluation Metrics:
    📐 IoU (Intersection over Union)
    🎯 F1-Score
    📊 Precision
    🔁 Recall

✅ Why Use Overlapping Patches?
    ✔️ Prevents edge artifacts
    ✔️ Improves prediction smoothness
    ✔️ Better segmentation of small and fine features

📂 Output Samples
Input (Grayscale)	Predicted Mask	Vector Polygons

📎 Data Source
Download CORONA data from USGS EarthExplorer

📜 License
This project is open-source and available under the MIT License.

📌 Conclusion:
  This project successfully demonstrates how deep learning can be applied to historic satellite imagery for meaningful land use analysis. 
  By leveraging a U-Net segmentation model on CORONA grayscale data (1967), we achieved accurate detection of agricultural land with strong evaluation metrics (IoU, F1-score, Precision, Recall).
    🔍 This method offers a valuable tool for:
          Analyzing historical cropland patterns
          Supporting policy research on agricultural expansion or decline
          Enabling change detection across decades using archival imagery
          The approach highlights the power of AI in geospatial analysis, even with limited or low-band satellite data.
    
  🚀 This framework can be extended to other historical datasets, regions, or land cover types with minimal adjustments.



