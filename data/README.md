# SafeSite Dataset Info

**Source:** We pulled this data from the Roboflow Universe public datasets. It focuses specifically on construction workers and personal protective equipment (PPE).

**Quick Stats:**
* **Total Images:** ~2,500 images (already split into train, validation, and test folders).
* **Format:** YOLOv8 PyTorch format (meaning every image has a matching `.txt` file with the bounding box coordinates).
* **Classes:**
  0: `Helmet`
  1: `No-Helmet`
  2: `Vest`
  3: `No-Vest`

**Notes on Prep:**
We aren't doing any manual labeling since the Roboflow community already handled it. During training, our YOLO script will automatically resize all these images to 640x640 pixels.