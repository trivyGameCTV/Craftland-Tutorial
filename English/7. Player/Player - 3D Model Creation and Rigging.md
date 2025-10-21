### **Step 1: Generate a 2D Character Image**

Start by creating a concept art or character image using an AI image generator. Some popular tools include:

* **ChatGPT (with image tools enabled)**

* **DALL·E**

* **Midjourney**

* **Stable Diffusion**

Example:

Input:  Recreate this image in a 3D chibi style. Remove the gun from the image above, and then provide me 3 images from 3 different angles of the image above. Give me a version of the image above where the model is T-Posing

![image-3d-model-1](https://github.com/trivyGameCTV/Craftland-Tutorial/blob/main/English/7.%20Player/img/image-3d-model-1.png)

Output:

![image-3d-model-2](https://github.com/trivyGameCTV/Craftland-Tutorial/blob/main/English/7.%20Player/img/image-3d-model-2.png)

---

### **Step 2: Convert the 2D Image to a 3D Model with Tripo AI**

Next, upload your generated 2D image to [**Tripo AI**](https://tripo.ai). It will automatically generate a basic 3D mesh of your character.

* Visit [tripo.ai](http://tripo.ai)  
* Upload your image  
* Adjust custom tris count. For low poly game assets, use around 1000-2000  
* Download the resulting 3D model

Example: [https://drive.google.com/file/d/1AehToMISiN3\_aHnUYr14mNSh2DeU6Gd2/view?usp=sharing](https://drive.google.com/file/d/1AehToMISiN3_aHnUYr14mNSh2DeU6Gd2/view?usp=sharing)

---

### **Step 3: Rig and Animate the Model with Mixamo**

Now that you have a 3D mesh, head over to [**Mixamo**](https://www.mixamo.com/) to rig it:

1. Upload the 3D model file

2. Use the auto-rigging tool (you’ll need to place markers on the chin, wrists, elbows, knees, and groin)

3. After rigging, choose from a variety of pre-made animations

4. Download the rigged and animated model

Example: [https://drive.google.com/file/d/1yX0kxsTGH86eQq66AoXoovYxeOBp5xwl/view?usp=sharing](https://drive.google.com/file/d/1yX0kxsTGH86eQq66AoXoovYxeOBp5xwl/view?usp=sharing)

---

### **Step 4: Extract Texture**

Because Craftland Studio can’t read mat file, so we need to extract the texture from the model first.

1. Open Blender  
2. Import the Rigged model  
3. Select UV editing tab  
4. Save the texture.

Example: [https://drive.google.com/file/d/1spVf5\_0s5iDRO5wA7pxTzLUriS-XigkN/view?usp=sharing](https://drive.google.com/file/d/1spVf5_0s5iDRO5wA7pxTzLUriS-XigkN/view?usp=sharing)

### **Step 5: Import into Craftland Studio**

Finally, bring your character into **Craftland Studio**:

1. Open Craftland Studio  
2. Import the rigged model  
3. Create a mat file for the extracted texture in step 4\.  
4. Apply mat for the model and create prefab  
5. Create a playerdata file and select the prefab, add any animation you want.  
6. Add the playerdata file to the player module.

Example: [https://drive.google.com/file/d/1UnlZLHS6TjQQtWLN1EGKdFc9QtTB2x-7/view?usp=sharing](https://drive.google.com/file/d/1UnlZLHS6TjQQtWLN1EGKdFc9QtTB2x-7/view?usp=sharing)