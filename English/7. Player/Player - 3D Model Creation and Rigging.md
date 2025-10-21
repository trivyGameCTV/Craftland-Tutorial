### **Step 1: Generate a 2D Character Image**

Start by creating a concept art or character image using an AI image generator. Some popular tools include:

* **ChatGPT (with image tools enabled)**

* **DALL·E**

* **Midjourney**

* **Stable Diffusion**

Example:

Input:  Recreate this image in a 3D chibi style. Remove the gun from the image above, and then provide me 3 images from 3 different angles of the image above. Give me a version of the image above where the model is T-Posing

|Input|Output|
|-----|------|
|![image-3d-model-1](https://github.com/trivyGameCTV/Craftland-Tutorial/blob/main/English/7.%20Player/img/image-3d-model-1.png)|![image-3d-model-2](https://github.com/trivyGameCTV/Craftland-Tutorial/blob/main/English/7.%20Player/img/image-3d-model-2.png)|

---

### **Step 2: Convert the 2D Image to a 3D Model with Tripo AI**

Next, upload your generated 2D image to [**Tripo AI**](https://tripo.ai). It will automatically generate a basic 3D mesh of your character.

* Visit [tripo.ai](http://tripo.ai)  
* Upload your image  
* Adjust custom tris count. For low poly game assets, use around 1000-2000  
* Download the resulting 3D model

Example:


https://github.com/user-attachments/assets/4a3e617f-0090-4466-a105-848d12073ecc

---

### **Step 3: Rig and Animate the Model with Mixamo**

Now that you have a 3D mesh, head over to [**Mixamo**](https://www.mixamo.com/) to rig it:

1. Upload the 3D model file

2. Use the auto-rigging tool (you’ll need to place markers on the chin, wrists, elbows, knees, and groin)

3. After rigging, choose from a variety of pre-made animations

4. Download the rigged and animated model

Example:

https://github.com/user-attachments/assets/c572a796-a786-4e57-aec0-e6d8db6c460c

---

### **Step 4: Extract Texture**

Because Craftland Studio can’t read mat file, so we need to extract the texture from the model first.

1. Open Blender  
2. Import the Rigged model  
3. Select UV editing tab  
4. Save the texture.

Example:

https://github.com/user-attachments/assets/e4879d23-0738-40a9-81e3-7ee8b16ccdf0

---

### **Step 5: Import into Craftland Studio**

Finally, bring your character into **Craftland Studio**:

1. Open Craftland Studio  
2. Import the rigged model  
3. Create a mat file for the extracted texture in step 4\.  
4. Apply mat for the model and create prefab  
5. Create a playerdata file and select the prefab, add any animation you want.  
6. Add the playerdata file to the player module.

Example:

https://github.com/user-attachments/assets/bbeaa72c-1f77-425c-850b-c95278ddfc2e
