---
title: IdP SSO Integration Guide
description: Step-by-step guide to configure SSO Connection with Identity Provider in SSOJet
---

This guide walks you through setting up an SSO connection as a SAML Identity Provider (IdP) for your application using SSOJet.

## Prerequisites

- Access to your Identity Provider (IdP) account
- SSOJet account with admin privileges or an active Admin Portal link

An Admin Portal link serves as the gateway for enterprise users to access their Admin Portal. Each link is generated using a Tenant ID, ensuring that only resources within the specified tenant can be managed during a portal session.

When making an API call to generate an Admin Portal link, you must specify a time duration. For security reasons, keep portal link expiry short. To prevent access issues, users should be redirected immediately rather than receiving the link via email.

## Supported Identity Providers

We supports a wide range of identity providers for SSO integration. Below is the list of supported IdPs:

# Supported Identity Providers for SSO Integration

Below is the list of supported IdPs:

<table style="width: 100%;">
  <tr>
    <th style="border: 1px solid #d6d0d0; padding: 10px; align-content: center; width: 300px;text-align: center;">
      Identity Provider
    </th>
    <th style="border: 1px solid #d6d0d0; padding: 10px; align-content: center;width:300px;padding:12px;">
      Logo
    </th>
  </tr>
  <tr>
    <td style="border: 1px solid #d6d0d0; padding: 10px; align-content: center;width: 300px;text-align: center;">
      Okta
    </td>
    <td style="border: 1px solid #d6d0d0; padding: 10px; align-contentn: center;width: 300px;text-align: center;padding:12px;">
      <img
        src="https://cdn.ssojet.com/ssoproviders/okta.png"
        alt="Okta"
        width="100"
      />
    </td>
  </tr>
  <tr>
    <td style="border: 1px solid #d6d0d0; padding: 10px; align-content: center;width: 300px;text-align: center;">
      OneLogin
    </td>
    <td style="border: 1px solid #d6d0d0; padding: 10px; align-content: center;width: 300px;text-align: center;padding:12px;">
      <img
        src="https://cdn.ssojet.com/ssoproviders/onelogin.png"
        alt="OneLogin"
        width="100"
      />
    </td>
  </tr>
  <tr>
    <td style="border: 1px solid #d6d0d0; padding: 10px; align-content: center;width: 300px;text-align: center;">
      Microsoft Entra ID (Azure AD)
    </td>
    <td style="border: 1px solid #d6d0d0; padding: 10px; align-content: center;width: 300px;text-align: center;padding:12px;">
      <img
        src="https://cdn.ssojet.com/ssoproviders/entra-id.png"
        alt="Microsoft Entra ID"
        width="100"
      />
    </td>
  </tr>
  <tr>
    <td style="border: 1px solid #d6d0d0; padding: 10px; align-content: center;width: 300px;text-align: center;">
      Google Workspace
    </td>
    <td style="border: 1px solid #d6d0d0; padding: 10px; align-content: center;width: 300px;text-align: center;padding:12px;">
      <img
        src="https://cdn.ssojet.com/ssoproviders/google-workspace.png"
        alt="Google Workspace"
        width="100"
      />
    </td>
  </tr>
  <tr>
    <td style="border: 1px solid #d6d0d0; padding: 10px; align-content: center;width: 300px;text-align: center;">
      Ping Identity
    </td>
    <td style="border: 1px solid #d6d0d0; padding: 10px; align-content: center;width: 300px;text-align: center;padding:12px;">
      <img
        src="https://cdn.ssojet.com/ssoproviders/pingidentity.png"
        alt="Ping Identity"
        width="100"
      />
    </td>
  </tr>
  <tr>
    <td style="border: 1px solid #d6d0d0; padding: 10px;align-content: center;width: 300px;text-align: center;">
      Auth0
    </td>
    <td style="border: 1px solid #d6d0d0; padding: 10px; align-content: center;width: 300px;text-align: center;padding:12px;">
      <img
        src="https://cdn.ssojet.com/ssoproviders/auth0.png"
        alt="Auth0"
        width="100"
      />
    </td>
  </tr>
  <tr>
    <td style="border: 1px solid #d6d0d0; padding: 10px; align-content: center;width: 300px;text-align: center;">
      JumpCloud
    </td>
    <td style="border: 1px solid #d6d0d0; padding: 10px; align-content: center;width: 300px;text-align: center;padding:12px;">
      <img
        src="https://cdn.ssojet.com/ssoproviders/jumpcloud.png"
        alt="JumpCloud"
        width="100"
      />
    </td>
  </tr>
  <tr>
    <td style="border: 1px solid #d6d0d0; padding: 10px; align-content: center;width: 300px;text-align: center;">
      Duo
    </td>
    <td style="border: 1px solid #d6d0d0; padding: 10px; align-content: center;width: 300px;text-align: center;padding:12px;">
      <img
        src="https://cdn.ssojet.com/ssoproviders/duo.png"
        alt="Duo"
        width="100"
      />
    </td>
  </tr>
  <tr>
    <td style="border: 1px solid #d6d0d0; padding: 10px; align-content: center;width: 300px;text-align: center;">
      Salesforce
    </td>
    <td style="border: 1px solid #d6d0d0; padding: 10px; align-content: center;width: 300px;text-align: center;padding:12px;">
      <img
        src="https://cdn.ssojet.com/ssoproviders/salesforce.png"
        alt="Salesforce"
        width="100"
      />
    </td>
  </tr>
  <tr>
    <td style="border: 1px solid #d6d0d0; padding: 10px; align-content: center;width: 300px;text-align: center;">
      CyberArk Identity
    </td>
    <td style="border: 1px solid #d6d0d0; padding: 10px; align-content: center;width: 300px;text-align: center;padding:12px;">
      <img
        src="https://cdn.ssojet.com/ssoproviders/cyberark.png"
        alt="CyberArk Identity"
        width="100"
      />
    </td>
  </tr>
  <tr>
    <td style="border: 1px solid #d6d0d0; padding: 10px; align-content: center;width: 300px;text-align: center;">
      ForgeRock
    </td>
    <td style="border: 1px solid #d6d0d0; padding: 10px; align-content: center;width: 300px;text-align: center;padding:12px;">
      <img
        src="https://cdn.ssojet.com/ssoproviders/forgerock.png"
        alt="ForgeRock"
        width="100"
      />
    </td>
  </tr>
  <tr>
    <td style="border: 1px solid #d6d0d0; padding: 10px; align-content: center;width: 300px;text-align: center;">
      Custom SAML Provider
    </td>
    <td style="border: 1px solid #d6d0d0; padding: 10px; align-content: center;width: 300px;text-align: center;padding:12px;">
      <img
        src="https://cdn.ssojet.com/ssoproviders/saml.png"
        alt="Custom SAML Provider"
        width="100"
        height="50"
      />
    </td>
  </tr>
</table>

## Configuration Steps

### 1. Get Admin Portal Link

To configure an SSO connection, you first need an IT Admin Portal link. The Admin Portal allows IT admins to manage authentication settings. Since the method of generating the link depends on the customer’s implementation, here’s a general example of the process:

**Example Process to Generate Admin Portal Link:**

1. Navigate to your customer dashboard.
2. Locate the **Admin Portal Access** section.
3. Provide the required expiration time for IT Admin Portal link.
4. Generate the IT Admin Portal link.
5. Copy and use the link to access the IT Admin Portal.

### 2. Setup SSO Connection using IT Admin Portal

Once inside the Admin Portal, follow these steps:

#### Step 1: Open Admin Portal URL

- Visit the generated Admin Portal link.
- The portal will provide two options:
  1. **SSO Configuration**
  2. **SCIM Connection Configuration**
- Select **SSO Configuration**.
  ![Access SAML](https://cdn.ssojet.com/ssoproviders/ssojet-single-sign-on-widget.png)

#### Step 2: Select Identity Provider

- A list of supported IdP providers will be displayed.
- Choose the provider that your organization uses.
  ![Access SAML](https://cdn.ssojet.com/ssoproviders/ssojet-single-sign-on-widget-providers.png)

#### Step 3: Configure Identity Provider Settings

- Follow the step-by-step instructions provided in the portal to complete the setup.

![Access SAML](https://cdn.ssojet.com/ssoproviders/ssojet-single-sign-on-widget-providers-steps.png)

### 3. Validate and Enable SSO

1. Save the configured settings.
2. Use **Test Connection** to verify SSO authentication.
3. Once validated, enable SSO for your users.

### Troubleshooting

- Ensure correct ACS URL and Entity ID are used.
- Verify metadata file is correctly uploaded.
- Check user assignment and attribute mapping.
- Review IdP logs for authentication failures.

---

Following these steps, you can successfully integrate SSO with your chosen IdP using SSOJet.
