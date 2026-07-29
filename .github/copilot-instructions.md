## Copilot instructions for Cloud Volumes ONTAP documentation

### Repository overview
Product: Cloud Volumes ONTAP

This repository contains release notes for *Cloud Volumes ONTAP* across AWS, Azure, and Google Cloud. The content focuses on release changes, supported configurations, storage limits, licensing, known issues, limitations, and cloud provider integration behavior.

### Repository structure
- Top-level AsciiDoc pages for the current release, including *What's new*, licensing, provider-specific supported configurations, storage limits, known issues, limitations, and provider integrations.
- `_include/` – Reusable include fragments for shared licensing and capacity-limit content referenced from multiple pages.
- `media/` – Shared PDF notices and other assets linked from the release-notes pages.

### Product-specific context
**Architecture and components:**
- *Cloud Volumes ONTAP* runs in public cloud infrastructure and is documented here for AWS, Azure, and Google Cloud.
- Deployments are either *single-node* systems or *high-availability (HA) pairs*; HA is described as providing fault tolerance and nondisruptive operations.
- The *NetApp Console* is the management layer for deployment, upgrades, disks, and aggregates; the docs explicitly say not to use cloud-provider consoles, *System Manager*, or the CLI for those changes.
- Capacity can combine cloud disks with object storage used for data tiering, depending on the license and provider-specific support matrix.
- Some supported VM or instance types use local NVMe or LSSD storage as *Flash Cache*.

**Key concepts:**
- *Licensing* is described with capacity-based packages, *Keystone Flex Subscription*, and node-based models that still appear in configuration matrices.
- *Aggregates* and disks are managed from the *Console* and are part of the supported configuration and storage-limit guidance.
- *Object storage tiering* extends system capacity by moving inactive data to services such as *S3* or *Google Cloud Storage* where supported.
- *Snapshot copies* mean ONTAP Snapshot copies; the docs explicitly say cloud-provider snapshots should not be used for backup and recovery of Cloud Volumes ONTAP data.
- *Known limitations* include unsupported ONTAP features and provider-specific deployment constraints, especially around HA behavior and VM or instance restrictions.

**Naming conventions and terminology:**
- *HA* means *high availability*; the repo also distinguishes *single-node* versus *HA pair* deployments.
- *Console* or *NetApp Console* is the control plane referenced for deployment, upgrades, and storage management.
- License terms used in the repo include *Freemium*, *PAYGO*, *BYOL*, *Essentials*, *Professional*, and *Keystone Flex Subscription*.
- Provider-specific compute terms are preserved as written: *EC2 instance types* in AWS, *VM types* in Azure, and *machine types* or *VMs* in Google Cloud.
- Storage and data-protection terms appear with specific technical meaning, including *Flash Cache*, *high write speed*, *SnapMirror*, *SnapVault*, *SMB Continuous Availability (CA)*, and *WAFL*.
- Provider-specific release-note files follow patterns such as `reference-configs-{provider}.adoc`, `reference-limits-{provider}.adoc`, and `reference-limitations-{provider}.adoc`.

### Typical user workflows
**Plan a deployment:** Choose cloud provider → Choose *single-node* or *HA pair* architecture → Select license model → Confirm supported VM or instance and storage options → Review provider-specific limits and limitations

**Upgrade a system:** Review *What's new* and limitations → Check whether the release is available for the target cloud/provider path → Upgrade from the *NetApp Console* → Verify downtime or nondisruptive HA behavior

**Troubleshoot supportability:** Check known issues → Review common and provider-specific limitations → Confirm the deployment still uses supported resources and management paths → Coordinate with NetApp Support and the cloud provider when needed
