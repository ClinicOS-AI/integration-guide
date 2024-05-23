## Onboarding Form: Integration Guide
This guide walks through the integration steps for the embedding the Onboarding Form experience into a clinic website.

### Prerequisites
- ClinicOS SDK Key
- (Optional) Hex color for the theme

### Embed the ClinicOS Form script
Embed the following script in the html body of the site, replacing placeholders with actual values:

```HTML
<script src="https://www.clinic-os.com/clinicos-full-form-prod-v2.js" formName="onboarding-tier1"
 themeColor="<hex_color>" clinicSdkKey="<your_sdk_key>"></script>
 ```

### Example

Sample SDK Key: `768a5798-d8e1-432b-a5fe-c647ea7fc729`

Sample Hex Color: `#FF5733`

```HTML
<script src="https://www.clinic-os.com/clinicos-full-form-prod-v2.js" formName="onboarding-tier1"
 themeColor="#FF5733" clinicSdkKey="768a5798-d8e1-432b-a5fe-c647ea7fc729"></script>
 ```
