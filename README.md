# Image-to-Text-Extractor-
Image to Text Extractor usingb Tesseract

ppt: https://app.presentations.ai/view/BgelNG

I'll first extract the contents of the ZIP file and check the code inside. Then, I'll explain it in detail for your presentation.

The ZIP file contains a folder named **"Code"**. I'll check its contents and extract the relevant code files for explanation.

The folder contains a Python script named **"main.py"**. I'll now open and analyze its contents to explain the code.

### **Explanation of the Code (main.py)**  

This Python script is a **GUI-based application** that extracts text from images using **Tesseract OCR (Optical Character Recognition)** and **OpenCV**. It uses **Tkinter** for the graphical user interface.

---

### **Key Components of the Code:**

1. **Importing Necessary Libraries:**
   ```python
   from tkinter import *
   from tkinter import filedialog
   from PIL import ImageTk, Image
   import cv2
   import pytesseract
   ```
   - **Tkinter**: Used to create the GUI for selecting and displaying images.
   - **PIL (Pillow)**: Used for handling images in the GUI.
   - **OpenCV (cv2)**: Used for reading and processing images.
   - **Pytesseract**: Used to extract text from images.

2. **Setting Up Tesseract Path:**
   ```python
   pytesseract.pytesseract.tesseract_cmd = 'C:\\Program Files (x86)\\Tesseract-OCR\\tesseract.exe'
   ```
   - This sets the path to the Tesseract OCR executable, which is required to perform text extraction.

3. **Creating the GUI Window:**
   ```python
   root = Tk()
   root.title('TechVidvan Text from Image Project')
   ```
   - Initializes the Tkinter window with a title.

4. **Defining the `extract()` Function:**
   ```python
   def extract(path):
       Actual_image = cv2.imread(path)
       Sample_img = cv2.resize(Actual_image, (400,350))
       Sample_img = cv2.cvtColor(Sample_img, cv2.COLOR_BGR2RGB)
       texts = pytesseract.image_to_data(Sample_img)
   ```
   - Reads the image using OpenCV.
   - Resizes the image to a smaller size for better processing.
   - Converts the image from **BGR (OpenCV default) to RGB**.
   - Extracts text data from the image using **Pytesseract**.

5. **Processing Text from Image:**
   ```python
   for cnt, text in enumerate(texts.splitlines()):
       if cnt == 0:
           continue
       text = text.split()
       if len(text) == 12:
           x, y, w, h = int(text[6]), int(text[7]), int(text[8]), int(text[9])
   ```
   - Iterates over the text extracted by Tesseract.
   - Extracts the **bounding box coordinates** (x, y, width, height) of detected text.

6. **Uploading Image via File Dialog:**
   ```python
   def open_file():
       file_path = filedialog.askopenfilename()
       extract(file_path)
   ```
   - Opens a file dialog to **select an image**.
   - Calls `extract()` to process the selected image.

7. **Creating GUI Buttons for Interaction:**
   ```python
   btn = Button(root, text="Upload Image", command=open_file)
   btn.pack()
   ```
   - Adds a button to upload an image.

---

### **How the Code Works (Presentation Points):**
1. **User opens the application** (Tkinter window).
2. **User clicks "Upload Image"** → Opens file dialog to select an image.
3. **Image is processed using OpenCV and Tesseract OCR**:
   - Image is resized and converted to RGB.
   - Text is extracted and displayed on the screen.
4. **Detected text is highlighted in the image** using bounding boxes.
5. **Final output**: Text from the image is displayed in the application.

---

### **Possible Enhancements:**
- Add **error handling** (e.g., invalid image selection).
- Improve **text display formatting**.
- Integrate **language selection for OCR**.
- Save extracted text as a **file (TXT, PDF, etc.)**.
