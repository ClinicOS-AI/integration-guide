### AI Photo Capture: Integration Guide

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
   
      const handleShowTorsoScan = (e) => {
        e.preventDefault();
        const modal = document.getElementById("torso-scan-modal-k28vew83vj");
        modal.style.display = "block";
      };
    
      const handleShowBodyScan = (e) => {
        e.preventDefault();
        const modal = document.getElementById("body-scan-modal-k28vew83vj");
        modal.style.display = "block";
      };
    
      return (
        <div>
          <button onClick={(e) => handleShowBodyScan(e)}>Show body scan</button>
          <button onClick={(e) => handleShowTorsoScan(e)}>Show torso scan</button>
        </div>
      );
    };
    
    export default YourReactComponent;

## Handling Captured Photo Data
After the user submits images using the form, the images are returned in the console.

### Data Structure
After users submit images, the data is structured as follows:
- Each object in the array represents one image, containing:
  - `presigned_url`: A URL for directly accessing the uploaded image. Valid for 30 minutes.
  - `image`: A Blob object containing the image data.
  - `viewType`: Describes the perspective of the image (e.g., "BODY_FRONT", "BODY_SIDE", etc.).

```javascript
[
  {
    presigned_url: "https://production-us-east...",
    image: Blob,
    viewType: "BODY_FRONT"
  },
  {
    presigned_url: "https://production-us-east...",
    image: Blob,
    viewType: "BODY_LEFT"
  },
  {
    presigned_url: "https://production-us-east...",
    image: Blob,
    viewType: "BODY_RIGHT"
  },
  {
    presigned_url: "https://production-us-east...",
    image: Blob,
    viewType: "BODY_BACK"
  }
]
```

### Recommended Usage
- **Uploading Images**:
  - **Method 1**: Directly upload the Blob to your server for processing or storage.
  - **Method 2**: Use the presigned URL to access or download the image server-side.

### Example: Uploading a Blob to Your Server
Here's how you might upload an image Blob to your server using JavaScript:

```javascript
async function uploadImage(blob) {
  const formData = new FormData();
  formData.append("file", blob);

  try {
    const response = await fetch('YOUR_SERVER_ENDPOINT', {
      method: 'POST',
      body: formData,
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
