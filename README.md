# MindAR JS – Image Tracking with Zoom & Rotation (Gesture Controls)

This project demonstrates **gesture-based zooming and rotating** of a 3D model in **MindAR.js** using A-Frame.  
It also showcases a practical technique for **tracking only a specific part of a larger image** by generating a MindAR target from a cropped region.

---

## 🚀 Overview

The AR experience loads a **Bowser.glb** 3D model and allows users to:

- **Pinch to zoom in/out**
- **Drag with one finger to rotate** the model on X and Y axes
- Automatically detect when the tracking target is visible  
- Show a floating **status indicator** + **gesture hint**

All gesture logic is implemented directly in **index.html** using custom A-Frame components:
- `gesture-detector` – listens to touch events on the scene  
- `gesture-handler` – applies scale/rotation updates to the 3D model  

---

## 🖼️ Cropped Image Target Tracking

The AR target file `targets.mind` was generated from **only a cropped section** of the larger image `Graphic-Recording.png`.

Process:

1. A region of interest was cropped and saved as `tracked_image.png`
2. This cropped image was used in the MindAR compiler
3. MindAR now detects **just that part** even when scanning the full original image

This demonstrates a useful real-world AR pattern:

### 🎯 Track only the part you need  
Instead of tracking a big poster or full artwork, you can:
- Crop the exact region  
- Use that as the `.mind` target  
- Trigger AR content only on that part

---

## 📁 Project Structure

/
├── Bowser.glb # 3D model used in AR
├── index.html # Main AR scene + gesture controls
├── targets.mind # MindAR target generated from cropped image
├── Graphic-Recording.png # Original large image
└── tracked_image.png # Cropped region used to generate targets.mind


---

## 🧩 Key Features

### ✔️ Gesture Interaction (built-in code)
- **Pinch zooming**
- **Horizontal + vertical rotation**
- Real-time scaling with clamping limits (`minScale` / `maxScale`)
- Smooth gesture detection using touch events

### ✔️ Status & UX Elements
- “Target Detected / Scanning…” indicator  
- Pulsing detection dot  
- Gesture hint overlay (“Pinch to zoom • One finger to rotate”)  

### ✔️ Clean MindAR Setup
- A-Frame 1.7.1 + MindAR 1.2.5  
- `mindar-image-target` for detection  
- Physically correct rendering enabled  

---

## 🔧 Running the Project

Host the files locally:

```bash
npx http-server
```
Then open:

http://localhost:8080


Point your camera at tracked_image.png or at the full Graphic-Recording.png (MindAR will still detect the cropped region).
