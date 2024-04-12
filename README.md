### AI Photo Capture: Integration Guide

Follow these steps to integrate and set up your form:
1. **Adding the Script to Create Modal:**
   Add the following script inside the `<body>` tag of your HTML file, replacing placeholders with actual values:
   ```HTML
   <body>
     <!-- body content -->
   
     <script src="https://www.clinic-os.com/clinicos-scan-form.js" formName="onboarding-scan" themeColor="<hex_color>"
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
