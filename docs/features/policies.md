# Policies

OpenGRC provides comprehensive policy management capabilities to create, maintain, and track organizational security and compliance policies. Policies can be linked to controls, implementations, and risks for complete traceability.

## Overview

Policies in OpenGRC are organizational documents that define rules, guidelines, and standards for security and compliance. The policy management feature supports:

- Full policy lifecycle management (draft to retirement)
- Version control with revision history
- Document attachments (PDF, Word, DOCX)
- Linking to controls, implementations, and risks
- Department and scope classification
- Owner assignment and accountability

## Policy Attributes

Each policy includes the following information:

| Field | Description |
|-------|-------------|
| **Code** | Unique identifier (e.g., POL-001) |
| **Name** | Policy title |
| **Status** | Current lifecycle status |
| **Department** | Responsible department |
| **Scope** | Applicability scope |
| **Owner** | Policy owner (user) |
| **Effective Date** | When the policy takes effect |
| **Retired Date** | When the policy was retired (if applicable) |
| **Policy Scope** | Rich text describing what the policy covers |
| **Purpose** | Rich text describing why the policy exists |
| **Body** | Full policy content (rich text) |
| **Document** | Attached policy document file |
| **Revision History** | Version tracking with dates and changes |

## Policy Statuses

Policies progress through the following statuses:

| Status | Description |
|--------|-------------|
| **Draft** | Initial draft, not yet reviewed |
| **In Review** | Under review by stakeholders |
| **Awaiting Feedback** | Waiting for stakeholder input |
| **Pending Approval** | Awaiting formal approval |
| **Approved** | Officially approved and active |
| **Archived** | No longer active but retained for reference |
| **Superseded** | Replaced by a newer policy version |
| **Retired** | Permanently retired from use |

## Policy Scope Levels

Policies can be scoped to different organizational levels:

- **Organization-wide** - Applies to the entire organization
- **Department-specific** - Applies to a specific department
- **Project-specific** - Applies to a specific project
- **Regional** - Applies to a specific region
- **Global** - Applies globally across all entities

## Creating a Policy

### Step 1: Navigate to Policies
1. Go to **Policies** in the main navigation
2. Click **Create Policy**

### Step 2: Enter Core Information
1. **Code** - Enter a unique policy code or use auto-generated format
2. **Name** - Enter a descriptive policy name
3. **Status** - Select initial status (typically Draft)
4. **Department** - Select the responsible department
5. **Scope** - Select the applicability scope
6. **Owner** - Assign a policy owner
7. **Effective Date** - Set when the policy takes effect

### Step 3: Add Policy Content
1. **Policy Scope** - Describe what the policy covers
2. **Purpose** - Explain why this policy exists
3. **Body** - Enter the full policy content using the rich text editor

### Step 4: Attach Document (Optional)
Upload a policy document file:
- Supported formats: PDF, DOC, DOCX
- Maximum size: 10MB
- The document is stored securely and linked to the policy

### Step 5: Add Revision History
Track policy versions:
1. Click **Add Revision**
2. Enter version number (e.g., "1.0", "2.1")
3. Enter revision date
4. Enter author name
5. Describe the changes made

### Step 6: Save
Click **Create** to save the policy.

## Managing Policies

### Editing Policies
1. Navigate to the policy list
2. Click on a policy to view it
3. Click **Edit** to modify
4. Update fields as needed
5. Add a new revision history entry for significant changes
6. Save changes

### Viewing Policy Document
The policy detail view displays:
- Header with policy metadata (code, effective date, owner)
- Purpose section
- Scope section
- Full policy body content
- Attached document indicator
- Complete revision history table

### Linking to Controls
Associate policies with security controls:
1. Open the policy detail view
2. Go to the **Controls** tab
3. Click **Attach** to add controls
4. Search and select relevant controls
5. The policy now shows which controls it supports

### Linking to Implementations
Associate policies with implementations:
1. Open the policy detail view
2. Go to the **Implementations** tab
3. Click **Attach** to add implementations
4. Select implementations that enforce this policy

### Linking to Risks
Associate policies with risks they address:
1. Open the policy detail view
2. Go to the **Risks** tab
3. Click **Attach** to add risks
4. Select risks that this policy helps mitigate

## Version Control

### Adding Revisions
When updating a policy:
1. Open the policy for editing
2. Scroll to **Revision History**
3. Click **Add Revision**
4. Fill in:
   - **Version** - New version number
   - **Date** - Date of revision
   - **Author** - Who made the changes
   - **Changes** - Description of what changed
5. Save the policy

### Viewing Revision History
The revision history displays all versions chronologically, showing:
- Version number
- Revision date
- Author
- Summary of changes

## Filtering and Searching

### Search
Search policies by:
- Code
- Name
- Policy scope content
- Purpose content

### Filters
Filter the policy list by:
- **Status** - Draft, Approved, Archived, etc.
- **Scope** - Organization-wide, Department-specific, etc.
- **Department** - Responsible department
- **Has Document** - Whether a document is attached

### Sorting
Sort by any column including:
- Name
- Code
- Status
- Created date
- Updated date

## Permissions

| Permission | Capabilities |
|------------|--------------|
| **List Policies** | View the policy list |
| **Create Policies** | Create new policies |
| **Read Policies** | View policy details |
| **Update Policies** | Edit existing policies |
| **Delete Policies** | Remove policies |

Default role assignments:
- **Super Admin** - All permissions
- **Security Admin** - List, Create, Read, Update
- **Regular User** - List, Read only

## Best Practices

- **Use consistent naming** - Establish a naming convention for policy codes and titles
- **Set review schedules** - Plan regular policy reviews (annually recommended)
- **Track all changes** - Add revision history entries for every significant update
- **Link to controls** - Connect policies to the controls they support for traceability
- **Assign clear ownership** - Every policy should have an accountable owner
- **Archive don't delete** - Use Archive or Retired status instead of deleting policies
- **Keep documents current** - Update attached documents when policies change
