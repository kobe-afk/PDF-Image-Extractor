# 📄 PDF Image Extractor & Annotator

This project automates the **extraction, cropping, annotation, and renaming of images from PDF files**.  
It was built to replace a highly manual image-processing workflow and significantly reduce processing time.

---

## 🎯 Objective

To automate the extraction of images from PDF files and process them differently based on **file type**, including:
- Image cropping
- OCR-based text extraction
- Image annotation (superimposing values)
- Automated file renaming and saving

---

## 📂 Supported PDF File Types

### 1️⃣ Flatness Files
- Extracts **top view image** only
- Uses OCR to extract **ISO Flatness value**
- Superimposes ISO value onto the image

### 2️⃣ Roughness Files
- Extracts **top view image** only
- Uses OCR to extract **Sa value**
- Superimposes Sa value onto the image

### 3️⃣ BLD Files
- Extracts **top view (left & right)** and **side view**
- Uses OCR to extract **Y-distance value**
- Merges extracted views into a single image
- Superimposes extracted Y-distance value

---

## ⚙️ How It Works (High-Level Flow)

1. Walk through the directory to locate all PDF files  
2. Store file paths and metadata in a **DataFrame**
3. Extract the main image from each PDF
4. Detect file type (BLD / Flatness / Roughness)
5. Crop images based on file type
6. Extract required values using **OCR**
7. Resize and superimpose text onto images
8. Rename images using values from the DataFrame
9. Save processed images into the output folder

---

## 🧰 Requirements

### 📦 Python Libraries
Make sure the following libraries are installed:

- PyMuPDF  
- Pandas  
- OpenCV (`opencv-python`)  
- PyTesseract  

### 🖥️ External Dependency
- **Tesseract OCR (64-bit)**  
  Download from: https://github.com/UB-Mannheim/tesseract/wiki  

⚠️ Remember to update the **Tesseract executable path** inside the Python script.

---

## ▶️ How to Run

1. Download the following files:
   - `EXTRACTING_IMAGES_Ivan_v2.py`
   - `RUNNING.PY_FILE.ipynb`

2. Place both files in the directory containing the PDF files

3. Open `EXTRACTING_IMAGES_Ivan_v2.py` and update:
   - Path to the Tesseract executable

4. If `.py` cannot be run directly:
   - Launch **Jupyter Notebook**
   - Run `RUNNING.PY_FILE.ipynb`

---

## ⏱️ Performance & Time Savings

- ⏳ **~40% time saved per image**
- Reduced manual extraction and annotation effort
- Validated on sample runs of up to 5 images
- Time savings may increase with larger batches

---

## ⚠️ Limitations

- Script depends on:
  - Folder structure
  - Placement of `.py` file
- OCR accuracy varies depending on image quality
- Extracted filenames may require post-adjustment
- OCR processing can be time-consuming

---

## 📚 Challenges & Lessons Learned

### Challenges
- Cropping images without saving intermediate files
- Handling variations in folder structure
- Identifying file type from image content
- OCR speed and accuracy limitations
- Determining reliable crop coordinates

### Key Learnings
- Breaking problems into **smaller modular functions**
- Passing multiple parameters cleanly across functions
- Cropping images early improves OCR speed & accuracy
- Importance of robust and reusable functions
- Handling OCR output variability (`+`, `-`, `.`)

---

## 🚀 Future Improvements
- Further optimise OCR performance
- Improve filename accuracy
- Reduce dependency on folder structure
- Enhance robustness across more PDF variations
