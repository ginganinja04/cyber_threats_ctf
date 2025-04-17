# Individual CTF Report

**Author:** Maria Linkins-Nielsen  
**Course:** CSE 5272 - Cyber Threats  
**Challenge Link:** [CTF Challenge](https://ginganinja04.github.io/cyber_threats_ctf/)

---

## 1. Introduction

This report documents the design, implementation, and solution of a custom Capture the Flag (CTF) challenge focused on steganography and file analysis. The goal was to provide players with a realistic cybersecurity scenario involving embedded hidden data within an image file.

---

## 2. Objective

The objective of this project was to:

- Create a realistic and engaging scenario for cybersecurity students.
- Provide a challenge involving hidden data within an image.
- Allow players to utilize tools such as `binwalk`, `steghide`, and `exiftool` to uncover the hidden flag.

---

## 3. Challenge Overview

**Topic:** Steganography and File Analysis  
**Tools Used:**  
- `steghide`  
- `binwalk`  
- `exiftool`  
- `cat`  

**Challenge File:** `my_vacation.jpg`  
**Prompt:**  
> Our team intercepted a suspicious communication between two persons of interest. Attached was an image — seemingly a harmless photo from a tropical vacation.  
> At first glance, it appears to be just a vacation photo... but we believe there's more than meets the eye.  
> Your mission: Analyze the image file for hidden contents and extract the flag.

---

## 4. Creating the Challenge

### Step 1: Select Image 1  
A non-suspicious vacation photo was selected to serve as the main challenge file.

### Step 2: Select Image 2 / File to Hide  
A secondary file containing the flag was chosen.

### Step 3: Embed the Flag  
- Used `steghide` to embed the flag in the second file.
- Created a passphrase and embedded it in image metadata using `exiftool`.

### Step 4: Optional Obfuscation  
- Packaged the second file into a ZIP archive.

### Step 5: Final Embedding  
- Used `cat` to append the ZIP file to the main image file.

---

## 5. Hosting the Challenge

The challenge was hosted via GitHub Pages at:  
🔗 [https://ginganinja04.github.io/cyber_threats_ctf/](https://ginganinja04.github.io/cyber_threats_ctf/)


![image](https://github.com/user-attachments/assets/a6f2c3c9-c106-49b2-aa6d-25ed78f14eca)


---

## 6. Solving the Challenge

### Initial Analysis  
- The file appeared to be a standard JPEG.
![my_vacation](https://github.com/user-attachments/assets/9dcba25b-551e-4f49-a319-c298304807b4)
  

### Metadata Analysis  
- Ran `exiftool` and found a clue in the **XP Comment** field:  n0tJust4JPG
![image](https://github.com/user-attachments/assets/09190f90-433a-4c1e-af4d-a1d8b6b67673)

### File Carving & Extraction 

There are several methods to locate and extract hidden data:
- `binwalk -e my_vacation.jpg` (Used Method)
- `steghide extract -sf my_vacation.jpg`
- `dd if=my_vacation.jpg of=hidden.zip bs=1 skip=108850`
- Custom Python script (if applicable)


![image](https://github.com/user-attachments/assets/ba868d6e-1922-40a4-a77e-9e90db541cf2)


The ZIP archive contained a second image file:


![payload](https://github.com/user-attachments/assets/6713ac2d-4b15-4b12-91ae-95f707db2c33)




### Final Extraction  
- Using `steghide` with the password hint retrieved from metadata (`n0tJust4JPG`), the embedded ZIP was extracted.
- The flag was located inside the archive.

![image](https://github.com/user-attachments/assets/9580cb95-d3ac-4405-bbdd-bdd2c8c94df7)

![image](https://github.com/user-attachments/assets/e5346ed2-cab1-42d4-8769-3d95e5c45785)


### Submitting the Flag
Submitting the flag ----> FLAG{d0ubl3_l4y3r_d3c3pt10n}

![image](https://github.com/user-attachments/assets/e808644d-d77a-435b-adf8-feaa7726b8c8)



---

## 7. Conclusion

This challenge successfully demonstrated the principles of steganography, metadata exploitation, and file manipulation. It offered a hands-on opportunity to apply key forensic tools and techniques in a practical scenario.

---
