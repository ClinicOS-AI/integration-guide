## Onboarding Form: Integration Guide
This guide walks through the integration steps for the embedding the Onboarding Form experience on a clinic website. 

### Prerequisites
- ClinicOS SDK Key
- formName
- (Optional) Hex color for the theme
- (Optional) position
- (Optional) isCtaOpenByDefault
- (Optional) horizontalOffset
- (Optional) verticalOffset

### Embed the ClinicOS Form script
Embed the following script in the html body of the site, replacing placeholders with actual values:

```HTML
<script
    src="https://www.clinic-os.com/clinicos-full-form-prod-v2.js"
    clinicSdkKey="<your_sdk_key>"
    formName="onboarding-tier1"
    themeColor="<hex_color>"
    isCtaOpenByDefault="<true/false>"
    position="<left/right>"
    horizontalOffset="<pixels>"
    verticalOffset="<pixels>"
    ></script>
 ```

### Example

Sample SDK Key: `768a5798-d8e1-432b-a5fe-c647ea7fc729`

Sample Hex Color: `#FF5733`

Sample isCtaOpenByDefault: `true` or `false`

Sample position: `left` or `right`

Sample verticalOffset: `10px`

Sample horizontalOffset: `10px`

```HTML
<script src="https://www.clinic-os.com/clinicos-full-form-prod-v2.js"
    clinicSdkKey="768a5798-d8e1-432b-a5fe-c647ea7fc729"
    formName="onboarding-tier1"
    themeColor="#FF5733"
    isCtaOpenByDefault="true"
    position="right"
    horizontalOffset="20px"
    verticalOffset="20px"
    ></script>
 ```

### Embed the ClinicOS Form to a Button on Your Website
1. **Boilerplate for Creating Buttons to Open Modals (for React App):**
   Use this boilerplate code in your React component to create buttons that open respective modals:
   ```JSX
    import React from "react";
    
    const YourReactComponent = () => {
   
      const handleShowClinicosForm = (e) => {
        e.preventDefault();
        const modal = document.getElementById("visualize-the-new-you-k28vew83vj");
        modal.style.display = "block";
      };
    
      return (
        <div>
          <button onClick={(e) => handleShowClinicosForm(e)}>Show body scan</button>
        </div>
      );
    };
    
    export default YourReactComponent;
