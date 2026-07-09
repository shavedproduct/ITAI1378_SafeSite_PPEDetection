# SafeSite: Automated PPE Detection

**Team Members:** [Your Name], [Group Member 2], [Group Member 3]  
**Course:** ITAI 1378
**Project Tier:** Tier 1  

### Why Tier 1?
We chose Tier 1 because we want to focus on building a practical, working prototype within the 2-weeks or whenever its due. Using a pre-trained model (YOLOv8) on an existing dataset gives us enough time to actually train, test, and troubleshoot without getting stuck on data collection.

---

## The Problem
On big construction sites, safety managers can't physically watch every single worker all day. When people forget their hardhats or safety vests, it leads to bad accidents and huge OSHA fines. We need an automated way to spot these missing safety items so managers don't have to check manually.

## Our Solution
SafeSite is a computer vision system that acts like a second set of eyes. It takes photos or camera feeds from the site and uses object detection to find workers. It then checks if they are wearing their hardhat and vest. If someone is missing gear, the system puts a bounding box around them so supervisors can step in.

## Technical Plan
* **Method:** Object Detection
* **Model:** YOLOv8 (from Ultralytics)
* **Framework:** PyTorch
* **Why this setup?** YOLOv8 is fast and easy to get running. Since we need to detect things quickly (eventually in real-time), a heavy, slow model wouldn't make sense. The PyTorch/Ultralytics setup is also really well documented, which helps us troubleshoot errors faster.

## Data Plan
* **Source:** We are using a public construction dataset from Roboflow Universe.
* **Size:** About 2,500 labeled images.
* **Labels:** `Person`, `Helmet`, `No-Helmet`, `Vest`, `No-Vest`.
* **Prep:** The images are already labeled. We will just set our code to resize everything to 640x640 so it fits YOLO's default input size.

## Success Metrics
* **Primary (Accuracy):** We want to hit at least 80% mAP50 on our validation data.
* **Secondary (Speed):** We want it to process under 60ms per image on a Colab GPU, and under 800ms on a regular laptop CPU.

---

## 2-Week Plan

**Week 1: Setup & Baseline**
* Get the GitHub repo set up.
* Download the Roboflow dataset and format it.
* Run a baseline training session on Colab just to make sure the model actually learns something.

**Week 2: Tuning & Demo**
* Check the model's accuracy and add some image augmentations (like random cropping or brightness changes) if it's overfitting.
* Test the model on some random construction images from Google to see if it actually works.
* Clean up this repo, finish the slides, and record the demo.

---

## Resources
* **Hardware:** Google Colab (Free T4 GPU).
* **Software:** Python, PyTorch, Ultralytics, and OpenCV.
* **Budget:** $0. 

---

## Risks & Backup Plans

| Risk | Probability | What we will do about it |
| :--- | :--- | :--- |
| **Model memorizes the data (Overfitting):** It might do great on the training data but fail on new images. | High | We'll add messy images like horizontal flipping and color changes so the model sees more variety. |
| **Can't detect workers far away:** Small objects are hard for YOLO to see in wide shots. | Medium | We will focus our testing on "checkpoint" photos (like workers walking through a gate) instead of wide drone shots. |

---

## AI Usage Log
* Used google gemini to help brainstorm project ideas.
* Used AI to help format markdown tables and structure this README better than how i had it also helped with getting the data set setup and correcting a few things.