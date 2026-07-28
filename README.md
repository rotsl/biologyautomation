# Automation in Biology

This repository is the public submission, curation-tracking, documentation, and governance portal for the **Automation in Biology** community on Zenodo.

The community curates papers, software, datasets, protocols, book chapters, technical reports, hardware designs, presentations, and other scholarly outputs related to automation in biological research.

Zenodo remains the authoritative location for deposited files, metadata, licences, versions, DOIs, and community membership. GitHub provides structured submission issues, transparent curation status, validation, and the accepted-software registry.

## Submit a research output

Research outputs are deposited through Zenodo. This GitHub repository does not host submitted research files.

### Submission process

1. Sign in to Zenodo.
2. Create a new upload or open an existing published Zenodo record.
3. Submit the record to the **Automation in Biology** community.
4. Open a submission issue in this GitHub repository.
5. Include the Zenodo record URL and requested metadata.
6. Respond to any curator questions or requested changes.
7. After review, a maintainer applies the `zenodo-approve` label.
8. A protected GitHub Actions workflow accepts the pending Zenodo community-inclusion request, verifies public community membership, and applies the `accepted` label.
9. The accepted-registry workflow independently verifies membership and updates the public software registry.

[Open a GitHub submission issue](../../issues/new?template=submission.yml)

## Automated Zenodo curation

The repository includes a protected workflow for accepting reviewed Zenodo submissions:

```text
.github/workflows/accept-zenodo-community-request.yml
```

The workflow runs only when the repository owner applies the `zenodo-approve` label to an open submission issue. It:

1. Extracts exactly one Zenodo record URL from the issue.
2. Confirms the record is a published software output.
3. Confirms that the issue includes an external GitHub software repository.
4. Finds the open Zenodo `community-inclusion` request for the `biologyautomation` community.
5. Accepts the request using the protected `zenodo-production` environment.
6. Verifies that the record is publicly visible in the community.
7. Removes `zenodo-approve` and applies `accepted`.
8. Triggers the accepted-repository registry workflow.

The Zenodo API token is stored only as the `ZENODO_API_TOKEN` secret in the protected `zenodo-production` environment. Contributors must never provide API tokens, passwords, or private credentials to curators.

If automated acceptance is unavailable, a curator may accept the request manually in Zenodo. The `accepted` label must not be applied until public community membership has been verified.

## Submit software directly from GitHub

Software authors can use the native GitHub–Zenodo integration to archive a versioned GitHub release and request inclusion in the **Automation in Biology** community.

The integration must be configured in the repository containing the software, not in this community-administration repository.

### Step 1: Add `.zenodo.json`

Create a file named `.zenodo.json` in the root of the software repository.

At minimum, include the software creators, title, description, licence, keywords, and the Automation in Biology community identifier:

```json
{
  "title": "Name of the software",
  "description": "A clear description of the software and its role in automating biological research.",
  "upload_type": "software",
  "creators": [
    {
      "name": "Family name, Given name",
      "affiliation": "Institution name",
      "orcid": "0000-0000-0000-0000"
    }
  ],
  "license": "MIT",
  "keywords": [
    "automation in biology",
    "laboratory automation",
    "research software"
  ],
  "communities": [
    {
      "identifier": "biologyautomation"
    }
  ]
}
```

Replace all example metadata with accurate information for the software. The community identifier must remain:

```json
{
  "identifier": "biologyautomation"
}
```

### Step 2: Connect GitHub to Zenodo

The software repository owner must:

1. Sign in to Zenodo.
2. Link their GitHub account to Zenodo.
3. Open the **GitHub** section from their Zenodo profile menu.
4. Select **Sync now**.
5. Find the software repository.
6. Enable the repository using the toggle.

This must be configured by someone with the necessary access to the software repository and its Zenodo integration.

### Step 3: Create a GitHub release

After committing `.zenodo.json`, create a versioned GitHub release, for example:

```text
v1.0.0
```

Zenodo will detect the new release, archive the released source code, create a software record, and mint a DOI.

Creating commits or pushing ordinary branches is not sufficient. A published GitHub release is required.

### Step 4: Submit the record to the community

After Zenodo creates the record, submit the published record to the **Automation in Biology** community. This creates a pending Zenodo `community-inclusion` request for curator review.

The request is not automatically approved merely because `.zenodo.json` names the community. A curator may accept it, request metadata changes, or decline it if it is outside the community scope.

### Step 5: Open a tracking issue

Open a submission issue in this repository and provide:

- The Zenodo record URL
- The software repository URL
- The release version
- A description of its relevance to automation in biology

[Open a software submission issue](../../issues/new?template=submission.yml)

### Important limitations

The GitHub–Zenodo integration is intended primarily for software releases.

Use a normal Zenodo deposit for outputs such as:

- Papers
- Book chapters
- Datasets not distributed as software releases
- Posters
- Presentations
- Experimental protocols
- Hardware documentation requiring separately packaged files

Each contributor should enable the integration using their own GitHub and Zenodo accounts.

Contributors must never send Zenodo API tokens, GitHub credentials, passwords, or private access tokens to community curators.

## Eligible outputs

The community considers:

- Research papers and preprints
- Software and source code
- Research datasets
- Experimental protocols and workflows
- Book chapters
- Technical reports
- Posters and presentations
- Hardware designs and documentation
- Educational and training materials

Submissions must have a clear and substantial connection to automation in biological research.

Relevant topics include:

- Laboratory automation
- Robotic experimentation
- Automated sample preparation
- High-throughput experimentation
- Autonomous and self-driving laboratories
- Biofoundries
- Automated microscopy and phenotyping
- Automated biological data analysis
- Workflow-management systems
- Laboratory-information systems
- Scientific software and instrumentation
- Standards and interoperability
- Reproducible automated protocols
- Machine learning integrated with experimental workflows

## Important submission rules

- Submitters must deposit their own files through their own Zenodo account.
- Do not upload confidential, sensitive, personal, restricted, or unpublished research files to GitHub.
- A GitHub issue does not constitute acceptance into the Zenodo community.
- Applying `zenodo-approve` authorises the protected acceptance workflow; it is a curator-only action.
- Community inclusion is decided by the Zenodo community curators.
- Acceptance indicates relevance to the community scope; it is not peer review or scientific endorsement.
- Submitters remain responsible for authorship, licensing, ethics, privacy, copyright, and record accuracy.

## Documentation

- [Submission guide](docs/SUBMISSION_GUIDE.md)
- [Curation policy](docs/CURATION_POLICY.md)
- [Contributing guide](CONTRIBUTING.md)
- [Code of conduct](CODE_OF_CONDUCT.md)
- [Security policy](SECURITY.md)

## Zenodo community

**Community identifier:** `biologyautomation`

**Community URL:**  
https://zenodo.org/communities/biologyautomation

## Repository scope

This repository contains:

- Submission forms
- Documentation
- Validation workflows
- Protected Zenodo acceptance automation
- Public issue-based submission tracking
- Accepted-software registry automation
- Community governance information

It is not an archival repository for submitted research outputs. Zenodo is the authoritative location for deposited records, files, licences, versions, DOIs, and community membership.

## Licence

The documentation and templates in this repository are available under the MIT Licence included in the [LICENSE](LICENSE) file.

Research outputs deposited on Zenodo retain the licences selected by their respective depositors.

## Accepted repository registry

Accepted software repositories are recorded in two formats:

- [Accepted repositories](ACCEPTED_REPOSITORIES.md)
- [Machine-readable registry](accepted-repositories.json)

After the Zenodo acceptance workflow applies the `accepted` label, a second GitHub Actions workflow independently verifies that the record is publicly present in the `biologyautomation` community, opens a generated registry pull request, and merges that pull request after safety checks.
