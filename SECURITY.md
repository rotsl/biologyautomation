# Security policy

## Supported content

This repository contains documentation, GitHub issue forms, and GitHub Actions
workflows.

It does not accept research files as GitHub submissions.

## Reporting a vulnerability

Do not report vulnerabilities, credentials, confidential data, or sensitive
personal information in a public GitHub issue.

Use GitHub private vulnerability reporting:

https://github.com/rotsl/biologyautomation/security/advisories/new

For a security problem involving Zenodo itself, use Zenodo's official support
or security-reporting process.

## Accidental credential disclosure

If a credential is committed, pasted into an issue, or otherwise exposed:

1. Revoke or rotate it immediately.
2. Do not assume that deleting the file or issue makes the credential safe.
3. Remove sensitive material from repository history where necessary.
4. Review relevant access and audit logs.
5. Replace the credential everywhere it was used.
6. Document any unauthorised activity.

## GitHub Actions secrets

Any future API token must be stored as a GitHub Actions secret.

Never place API tokens in:

- Workflow YAML files
- README files
- Issue comments
- Pull-request descriptions
- Source-code files
- Example configuration files containing real credentials

## Public pull requests

Workflows handling pull requests from external contributors must not publish
records, modify external services, or expose privileged credentials.

A future Zenodo publishing workflow should only run through a trusted manual
trigger or another protected maintainer-controlled event.

## Research data

Do not commit:

- Identifiable participant data
- Confidential datasets
- Private keys
- Password files
- Restricted-access research materials
- Proprietary files without permission
- Unpublished sensitive information
