# Entra-ID
Understood! Let me provide a fully detailed explanation without reducing any information or size. Here's the comprehensive step-by-step guide:  

---

### **Step 1: Add Zendesk from the Gallery**

1. **Sign in to the Microsoft Entra Admin Center**:  
   - Visit the [Microsoft Entra Admin Center](https://portal.azure.com).  
   - Log in using an account with **Cloud Application Administrator** privileges.  

2. **Add Zendesk Application**:  
   - Navigate to **Identity > Applications > Enterprise Applications**.  
   - Click on **New Application**.  
   - In the **Add from Gallery** search box, type `Zendesk`.  
   - Select **Zendesk** from the results and click **Add**.  
   - Wait a few seconds for the application to be added to your tenant.
![Zendesk 1 ](https://github.com/user-attachments/assets/7df80447-5005-4a60-b00c-b25e9f7315c3)

---

### **Step 2: Create Test Users**

1. **Navigate to Users Section**:  
   - In the Microsoft Entra Admin Center, go to **Identity > Users > All Users**.  

2. **Create a New User**:  
   - Click **New User**.  
   - Fill in the required details:  
     - **Name**: Enter a name for the user.  
     - **Username**: Assign a unique username (e.g., `username@yourdomain.com`).  
     - **Password**: Either allow Microsoft to generate a temporary password or set one manually.  
   - Click **Create** to save the new user.
   ![zendesk 2 ](https://github.com/user-attachments/assets/c5a87f66-cc00-4977-a1b7-41e2d54be4cb)


---

### **Step 3: Assign Users to Zendesk**

1. **Access the Zendesk Application**:  
   - Navigate to **Identity > Applications > Enterprise Applications**.  
   - Click on **Zendesk** from the list of added enterprise applications.  

2. **Assign Users or Groups**:  
   - Select **Assign Users and Groups** from the application overview.  
   - Click **Add User/Group** in the **Add Assignment** dialog.  
   - In the **Users and Groups** selection screen, select the desired users (e.g., Judith, Darshan).  
   - Click **Select**, then click **Assign** to grant access to Zendesk.  

3. **Set a Role (Optional)**:  
   - If roles are configured for the application, choose one from the **Select a Role** dropdown.  
   - If no role is configured, the default access will apply.

---

### **Step 4: Configure Microsoft Entra SSO**

1. **Access SSO Settings**:  
   - In the Microsoft Entra Admin Center, go to **Identity > Applications > Enterprise Applications > Zendesk > Single Sign-On**.  

2. **Choose SAML Authentication**:  
   - On the **Select a single sign-on method** page, click **SAML**.  

3. **Configure Basic SAML Settings**:  
   - Click the pencil icon to edit the **Basic SAML Configuration**:  
     - **Identifier (Entity ID)**: `https://vosyn2349.zendesk.com`.  
     - **Reply URL (ACS URL)**: `https://vosyn2349.zendesk.com/access/saml`.  
     - **Sign-on URL**: `https://vosyn2349.zendesk.com`.  
   - Save the configuration.  

4. **Download SAML Signing Certificate**:  
   - Scroll down to the **SAML Signing Certificate** section.  
   - Click **Download Certificate (Base64)** and save the file securely.
  ![z 3](https://github.com/user-attachments/assets/bb2b5d16-b4ab-4a0e-a437-c6d37e17c7bc)
![z4](https://github.com/user-attachments/assets/c2847671-1ccd-4df8-a82b-7580888ad348)
![z5](https://github.com/user-attachments/assets/32934b45-0ac0-4fc9-9f7e-6711366f7bda)
![z6](https://github.com/user-attachments/assets/ef0894f1-783a-4650-9fd1-3197d376ccb9)

---

### **Step 5: Configure Zendesk SSO**

1. **Log in to Zendesk Admin Center**:  
   - Open a new browser window and log in to the Zendesk Admin Center as an administrator.
![z7](https://github.com/user-attachments/assets/e91be00a-fbc9-41e2-81cd-13374be35643)

     
2. **Add a SAML SSO Configuration**:  
   - Navigate to **Account > Security > Single Sign-On**.  
   - Click **Create SSO Configuration** and select **SAML**.  
   - Provide the following details:  
     - **Configuration Name**: Enter `Microsoft SSO`.  
     - **SAML SSO URL**: Paste the Login URL from the Microsoft Entra SSO configuration.  
       Example: `https://login.microsoftonline.com/<tenant-id>/saml2`.  
     - **Certificate Fingerprint**: Paste the Thumbprint value from the downloaded certificate.  
       Example: `B9AA4C9CE3B60E8EB3E777467F8B5F72DEFA7241`.  
     - **Remote Logout URL**: Paste the Logout URL from the Microsoft Entra SSO configuration.  
       Example: `https://login.microsoftonline.com/<tenant-id>/saml2`.

3. **Enable the Configuration**:  
   - Check the box for **Show button when users sign in** and label it `Microsoft SSO`.  
   - Click **Save** to finalize the configuration.  

4. **Assign SSO Configuration to Users**:  
   - Navigate to **Account > Security**.  
   - Assign the configuration to **Team Members** and **End Users**.  
   - Under **Authentication Settings**, enable **External Authentication**.  
   - Select **Microsoft SSO** as the authentication method and set it as the primary option.

       ![z9](https://github.com/user-attachments/assets/cbe0cf15-c916-48fe-9f3f-e858b0974d05)
       ![z10](https://github.com/user-attachments/assets/80262fc0-b6f5-4259-a724-2c4b689705ec)
       ![z11](https://github.com/user-attachments/assets/57daf59f-6685-477a-8ae5-65890712e7f0)

---

### **Step 6: Create Users in Zendesk**

1. **Add Team Members**:  
   - In the Zendesk Admin Center, go to **People > Team > Team Members**.  
   - Click **Create New Team Member**.  
   - Fill in the required details and assign roles like **Agent** or **Admin**.
  
   ![zendesk 15](https://github.com/user-attachments/assets/16ff0442-6de6-47a0-a9bc-c137c9562074)

   ![z13](https://github.com/user-attachments/assets/b7e60844-cef0-4ccc-93a2-c981abbd4be6)


   ---

### **Step 7: Test SSO**

1. **Test SSO from Microsoft Entra Admin Center**:  
   - In the Microsoft Entra Admin Center, navigate to **Identity > Applications > Enterprise Applications > Zendesk > Single Sign-On**.  
   - Click **Test this application** to validate the SSO flow.  

2. **Test SSO from My Apps**:  
   - Go to [Microsoft My Apps](https://myapplications.microsoft.com).  
   - Click on the **Zendesk** tile.  
   - Verify that it redirects to the Zendesk Sign-on URL and allows seamless login using SSO.  



