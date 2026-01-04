# Applications

OpenGRC provides application inventory management to track software applications used across the organization. Each application is linked to a vendor, enabling integrated third-party risk management.

## Overview

Application management in OpenGRC enables organizations to:

- Maintain a software application inventory
- Track application ownership and accountability
- Categorize applications by type and deployment model
- Manage application approval status
- Link applications to vendors for risk assessment
- Control shadow IT through approval workflows

## Application Attributes

Each application record includes:

| Field | Description |
|-------|-------------|
| **Name** | Application name |
| **Owner** | User responsible for the application |
| **Type** | Application type (SaaS, Desktop, Server, etc.) |
| **Status** | Approval status |
| **Vendor** | Vendor providing the application (required) |
| **URL** | Application URL or access point |
| **Description** | Detailed description of the application |
| **Notes** | Internal notes |
| **Logo** | Application logo image |

## Application Types

Applications are classified by deployment type:

| Type | Description |
|------|-------------|
| **SaaS** | Cloud-based software as a service |
| **Desktop** | Locally installed desktop application |
| **Server** | Server-based application |
| **Appliance** | Hardware/software appliance |
| **Other** | Other application types |

## Application Statuses

| Status | Description |
|--------|-------------|
| **Approved** | Application is approved for use |
| **Rejected** | Application is not approved for use |
| **Limited** | Application approved with restrictions |
| **Expired** | Application approval has expired |

## Vendor Requirement

Every application in OpenGRC **must be linked to a vendor**. This requirement ensures:

- All third-party software is tracked with its provider
- Vendor risk assessments cover associated applications
- Changes to vendor status affect related applications
- Complete visibility into vendor-application relationships

If an application's vendor is not yet in the system, add the vendor first before creating the application.

## Creating an Application

### Step 1: Ensure Vendor Exists
Before adding an application, verify the vendor exists:
1. Go to **Vendor Management**
2. Search for the vendor
3. If not found, create the vendor first

### Step 2: Navigate to Applications
1. Go to **Applications** in the main navigation
2. Click **Create Application**

### Step 3: Enter Application Details
1. **Name** - Enter the application name
2. **Owner** - Select the user responsible for this application
3. **Type** - Select the application type:
   - SaaS for cloud applications
   - Desktop for installed software
   - Server for server applications
   - Appliance for hardware appliances
   - Other for anything else
4. **Status** - Set the approval status
5. **Vendor** - Select the vendor (required)
6. **URL** - Enter the application URL if applicable
7. **Description** - Describe the application and its purpose
8. **Notes** - Add any internal notes
9. **Logo** - Upload the application logo (optional, max 1MB)

### Step 4: Save
Click **Create** to save the application.

## Managing Applications

### Viewing Applications
The application list displays:
- Application name
- Owner
- Type (color-coded badge)
- Vendor
- Status (color-coded badge)
- URL (clickable link)
- Created and updated dates

### Editing Applications
1. Click on an application to view it
2. Click **Edit** to modify
3. Update fields as needed
4. Save changes

### Changing Ownership
When an application owner leaves or changes roles:
1. Edit the application
2. Select a new owner
3. Save the change

The change is tracked in the activity log.

### Updating Status
As application approvals change:
1. Edit the application
2. Update the status:
   - **Approved** - Confirm continued approval
   - **Limited** - Add restrictions
   - **Rejected** - Revoke approval
   - **Expired** - Mark as expired
3. Add notes explaining the change
4. Save

## Application-Vendor Relationship

### Viewing Vendor's Applications
From a vendor detail page:
1. Go to the **Applications** tab
2. View all applications from this vendor
3. See each application's status and owner

### Vendor Status Impact
When a vendor's status changes, review associated applications:
- If vendor is **Rejected** - Consider rejecting related applications
- If vendor is **Terminated** - Plan application migration or replacement
- If vendor is **Expired** - Review and renew or replace applications

### Vendor Risk and Applications
High-risk vendors warrant additional scrutiny of their applications:
- Review data handling practices
- Assess security controls
- Consider alternative applications from lower-risk vendors

## Filtering and Searching

### Search
Search applications by:
- Name
- Owner name
- Vendor name

### Filters
Filter applications by:
- Type (SaaS, Desktop, Server, etc.)
- Status (Approved, Rejected, Limited, Expired)
- Vendor
- Owner

## Shadow IT Control

Use application management to control shadow IT:

1. **Document all applications** - Create records for all known applications
2. **Assign owners** - Ensure every application has an accountable owner
3. **Require approval** - Use status to track approval state
4. **Link to vendors** - Connect applications to vendor risk assessments
5. **Regular review** - Periodically audit the application inventory

### Handling Unapproved Applications
When discovering unapproved applications:
1. Create an application record with status **Rejected** or **Limited**
2. Document why it's not approved in notes
3. Identify the users using the application
4. Work with the owner to find an approved alternative
5. Plan migration or retirement

## Best Practices

- **Link all applications to vendors** - Ensure complete vendor visibility
- **Assign clear ownership** - Every application needs an accountable owner
- **Use appropriate types** - Categorize applications accurately for reporting
- **Review status regularly** - Keep approval status current
- **Document decisions** - Use notes to record approval reasoning
- **Connect to vendor assessments** - Consider vendor risk when approving applications
- **Track URLs** - Maintain accurate access URLs for reference
- **Upload logos** - Visual identification helps with application recognition
- **Audit periodically** - Regularly review the application inventory for accuracy
