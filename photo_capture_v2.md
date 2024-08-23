## AI Photo Capture: Integration Guide
This guide walks through the integration steps for the embedding just the Photo Capture expereince into an existing onboarding form.

Follow these steps to integrate and set up your form:
1. **Adding the Script to Create Modal:**
   Add the following script inside the `<body>` tag of your HTML file, replacing placeholders with actual values:
   ```HTML
   <body>
     <!-- body content -->
   
     <script src="https://www.clinic-os.com/clinicos-scan-form-prod.js" formName="onboarding-scan" themeColor="<hex_color>"
       clinicSdkKey="<your_sdk_key>"></script>
   
     <!-- body content -->
   </body>
   ```
2. **Accessing User Uploaded Images:**
   To receive data from the iframe, add the following code inside your React App:
   ```JSX
   import React, { useEffect } from "react";
   
   const YourReactComponent = () => {
   
     useEffect(() => {
       window.addEventListener("message", (ev) => {
         // Do something with your image data
         console.log(ev.data);
       });
     }, []);

     return (
       // Your JSX content
     );
   };
   
   export default YourReactComponent;
   ```


3. **Boilerplate for Creating Buttons to Open Modals (for React App):**
   Use this boilerplate code in your React component to create buttons that open respective modals:
   ```JSX
    import React from "react";
    
    const YourReactComponent = () => {
      
      const handleShowClinicosForm = (e, procedure) => {
       e.preventDefault();
       const procedureEvent = new CustomEvent("procedure-update", {
         detail: { procedure },
       });
       window.dispatchEvent(procedureEvent);
       const modal = document.getElementById("scan-modal-k28vew83vj");
       modal.style.display = "block";
      };
       
      return (
        <div>
          <button onClick={(e) => handleShowClinicosForm(e, "BREAST_AUGMENTATION")}>
            Open Scan Breast Augmnentation Form
          </button>
        </div>
      );
    };
    
    export default YourReactComponent;

3. **List of Available Procedures: The procedure parameters must be one of the following values:**
   ```JSX
   const availableProcedures = [
     "BBL",
     "TUMMY_TUCK",
     "BREAST_LIFT",
     "BREAST_REDUCTION",
     "BREAST_AUGMENTATION",
     "BREAST_LIFT_AND_AUGMENTATION",
     "BURN_REPAIR",
     "SCAR_REVISION",
     "HAND_SURGERY",
     "RECONSTRUCTIVE_SURGERY",
     "HAIR_TRANSPLANTATION",
     "BOTOX_INJECTIONS",
     "DERMAL_FILLERS",
     "LASER_TREATMENTS",
     "CHEMICAL_PEEL",
     "MICRODERMABRASION",
     "LASER_HAIR_REMOVAL",
     "THIGH_LIFT",
     "ARM_LIFT",
     "BUTTOCK_AUGMENTATION",
     "BODY_LIFT",
     "LIPOSUCTION",
     "CHEEK_AUGMENTATION",
     "CHIN_SURGERY",
     "FOREHEAD_LIFT",
     "OTOPLASTY",
     "RHYTIDECTOMY",
     "BLEPHAROPLASTY",
     "RHINOPLASTY",
     "RENUVION",
     "ABDOMINAL_ETCHING",
     "THIGH_LIPOSUCTION",
     "ARMS_LIPOSUCTION",
     "CHIN_LIPOSUCTION",
     "LABIAPLASTY",
     "VAGINAL_TIGHTENING",
     "VAGINAL_PRP",
     "HAIR_TRANSPLANT",
     "BIOCHETOMY",
     "FACE_LIFT",
     "CHIN_IMPLANT",
   ];


## Handling Captured Photo Data
After the user submits images using the form, the images are returned in the console.

### Data Structure
After users submit images, the data is structured as follows:
- Each object in the array represents one image, containing:
  - `image`: A Blob object containing the image data.
  - `viewType`: Describes the perspective of the image (e.g., "BODY_FRONT", "BODY_LEFT", etc.).

```javascript
{
  {
    presignedUrl: "https://production-us-east...",
    image: Blob,
    viewType: "BODY_FRONT"
  },
  {
    presignedUrl: "https://production-us-east...",
    image: Blob,
    viewType: "BODY_LEFT"
  },
  {
    presignedUrl: "https://production-us-east...",
    image: Blob,
    viewType: "BODY_RIGHT"
  },
  {
    presignedUrl: "https://production-us-east...",
    image: Blob,
    viewType: "BODY_BACK"
  }
}
```

### Recommended Usage
- **Uploading Images**:
  - **Method 1**: Directly upload the Blob to your server for processing or storage.
  - **Method 2**: Use the presigned URL to access or download the image server-side.

### Example: Uploading a Blob to Your Server
Here's how you might upload an image Blob to your server using JavaScript:

```javascript
async function uploadImage(data) {
  try {
    const response = await fetch('YOUR_SERVER_ENDPOINT', {
      method: 'POST',
      body: data,
    });
    if (response.ok) {
      console.log("Image uploaded successfully");
    } else {
      console.error("Upload failed");
    }
  } catch (error) {
    console.error("Error during the upload:", error);
  }
}
```
