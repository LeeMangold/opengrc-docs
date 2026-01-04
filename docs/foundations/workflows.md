# Typical Workflows

There are many ways to implement a Governance, Risk, and Compliance program. The following workflows form the basis of most SMB GRC programs and represent how OpenGRC is designed to work.

## Compliance Workflow

1. **Create a Standard** - Import or create the security framework you want to adhere to (e.g., NIST 800-171, ISO 27001)
2. **Review Controls** - Each standard contains controls (requirements) that define what must be done to achieve compliance
3. **Create Implementations** - Document how your organization satisfies each control requirement
4. **Perform Audits** - Regularly assess whether implementations are in place and operating effectively

## Internal Audit Workflow

Internal audits help you assess your security posture before external assessments or as part of continuous improvement.

1. **Define Scope** - Select the standard, program, or implementations to audit
2. **Create the Audit** - Initialize a new audit in OpenGRC
3. **Assess Each Item** - Review controls or implementations and assign a status (Compliant, Partially Compliant, Non-Compliant, Not Applicable)
4. **Document Findings** - Record observations, evidence, and recommendations
5. **Generate Reports** - Create audit reports for stakeholders and leadership
6. **Track Remediation** - Use findings to drive security improvements

## External Audit Workflow

External audits involve third-party assessors who need evidence packages and formal documentation.

1. **Import the IRL** - Load the auditor's Information Request List into OpenGRC to track their evidence requirements
2. **Create Data Requests** - Generate data requests for each IRL item and assign them to the appropriate control owners
3. **Collect Evidence** - Control owners respond to data requests with documentation, screenshots, and artifacts
4. **Review Submissions** - Verify that collected evidence addresses each requirement
5. **Export Evidence Package** - Download the complete evidence package (PDF files, zipped, with file hashes) for handoff to the external auditor
6. **Support the Assessment** - Provide additional clarification as auditors review the evidence

The key difference between internal and external audits is the formal evidence collection process. External audits require documented proof that can be verified and retained, which is why the IRL import and evidence export features are central to this workflow.

## Risk Management Workflow

OpenGRC allows you to manage, rank, and track cybersecurity risks in your environment. This straightforward risk management approach is sufficient for most small organizations.

1. **Create a Risk** - Document the risk scenario and potential impact
2. **Assess Inherent Risk** - Rate the risk based on likelihood and impact, assuming no controls are in place
3. **Link Implementations** - Associate implementations (mitigations) that reduce the likelihood or impact
4. **Assess Residual Risk** - Rate the risk again with mitigations applied
5. **Monitor and Review** - Use heatmaps to visualize risk posture and track changes over time

The goal is to reduce residual risk to an acceptable level based on your organization's risk appetite. While this workflow provides a solid foundation, comprehensive risk management may require additional processes beyond what is described here.