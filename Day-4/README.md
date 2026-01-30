# 100 Days of Cloud - Day 4

## Enable Versioning for S3 Bucket

# Overview 
<b>S3 Versioning</b> keeps <b>multiple variants of the same object</b> in a bucket. Every time you upload, overwrite, or delete an object, S3 preserves the previous version instead of replacing it permanently.

Think of it as built-in object revision history.

# How it works

- Each object gets a <b>Version ID</b>
- The latest version is returned by default when you GET an object
- Older versions remain stored and retrievable
- Deletes don’t actually remove data (unless you explicitly delete versions)

# Bucket versioning states

An S3 bucket can be in one of three states:

1. Unversioned (default)
- No version IDs
- Overwrites replace the object permanently
- Deletes permanently remove objects

2. Versioning Enabled
- All new objects get a unique Version ID
- Overwrites create new versions
- Deletes create a delete marker (object appears deleted, but data still exists)
3. Versioning Suspended
- Existing versions remain
- New objects are stored without version IDs
- Behaves partly like unversioned, but history isn’t lost

⚠️ Important: Once enabled, versioning can never be fully turned off, only suspended.

# Delete behavior (this trips people up)

When versioning is enabled:

- A normal delete adds a delete marker
- The object “disappears” from listings
- Older versions still exist and can be restored <br>

To permanently delete:
- You must delete each version explicitly, including the delete marker

Common use cases

- 🛡️Data protection / rollback (accidental deletes or overwrites)
- 🔐 Compliance & audit trails
- 🧪 Application version recovery
- 🧯 Ransomware recovery (especially with MFA Delete)

# Security & compliance features
- Works with S3 Object Lock (WORM compliance)
- Supports MFA Delete

Fully integrated with:

- IAM policies
- CloudTrail logging
- Replication (SRR / CRR)

# Versioning + Replication

With versioning enabled, S3 can replicate:
- All versions
- Delete markers (optional)
- Required for <b>Cross-Region Replication (CRR)</b>

# Pros & Cons

Pros

- Protects against accidental deletion
- Enables easy rollback
- Required for advanced features (replication, object lock)

Cons
- Higher storage cost
- Cleanup is more complex
- Deletes aren’t “real” deletes unless managed carefully

**Day 4 Complete!**