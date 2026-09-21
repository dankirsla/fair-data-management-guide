# A Practical FAIR Data Management Guide for Small Research Groups

FAIR stands for Findable, Accessible, Interoperable, and Reusable. The FAIR Guiding Principles are not a technical standard or a checklist that a dataset either passes or fails. They are a set of principles for making research data and other digital research objects easier for people and machines to discover, access, interpret, combine, and reuse.

That distinction matters in practice. A dataset can be publicly downloadable and still be difficult to reuse because nobody knows what its columns mean. Conversely, a dataset containing sensitive information may not be openly downloadable at all, but can still be managed in a FAIR way if its metadata are discoverable and the access conditions are clear.

This guide turns the principles into practical data-management habits for a small research group. It assumes a team of roughly two to eight researchers without a dedicated data manager and without a large infrastructure budget. The recommendations are deliberately general: the appropriate repository, metadata standard, file format, and access policy will depend on the research field.

If a funder requires a formal data management or data management and sharing plan, use the funder's current requirements first. For example, NSF requires a Data Management and Sharing Plan for proposals, while NIH currently requires a Data Management and Sharing Plan for research subject to its policy. NIH's 2026 format is substantially more structured than its previous format. This guide is therefore better treated as a working document for the research team than as a replacement for a funder's required template.

## Start with the data, not the repository

A common mistake is to choose a repository at the end of a project and then try to make the dataset fit its requirements. It is usually easier to make a few decisions at the beginning: what the files will contain, how variables will be described, who will be allowed to access them, and which person will be responsible for keeping the documentation current.

The formal plan does not need to be elaborate. A small group can keep a short project document describing the expected data, formats, storage location, access restrictions, documentation, repository, and responsibilities. Update it when the project changes rather than treating it as paperwork that is finished once the grant application is submitted.

For projects subject to a specific funder's rules, those rules take precedence. NSF and NIH requirements, for example, can change independently of the broader FAIR principles.

## Making data findable

The first problem for a future researcher is often simply locating the dataset.

A persistent identifier is useful here. A DOI is a common choice because repositories can assign one to a dataset and use it as a stable identifier in citations and metadata. The DOI itself does not guarantee that a dataset will remain available forever; the repository and its preservation policies still matter. What it provides is a persistent identifier and a standard way to retrieve the associated metadata.

The dataset record should also contain enough descriptive information to make it useful in a search. Instead of a title such as `Experiment 3 data`, use terms that another researcher would actually search for: the subject or organism, location, study type, instrument, or important variables. The same principle applies to the description.

Contributor identities are worth recording as well. ORCID identifiers can distinguish researchers who have similar names and can be associated with dataset records, publications, and other research outputs. ORCID is a practical implementation choice, not a separate FAIR requirement.

Repository indexing is another part of findability. If the project has a natural disciplinary repository, use it where appropriate. Otherwise, a general-purpose repository may be suitable. Services such as re3data can be used to locate repositories by subject, data type, and other characteristics. re3data is a registry of repositories; it is not itself a place to deposit the dataset.

The basic question to ask is simple: Could a researcher who has never met the project team discover that this dataset exists and determine whether it is relevant?

## Making data accessible

FAIR accessibility does not mean that every dataset has to be publicly downloadable.

The FAIR principles allow for authentication and authorization when access needs to be restricted. A dataset containing personal information, confidential research material, contractual information, or other sensitive data may therefore require an access-control process. What matters is that the retrieval method and conditions are understandable.

For an ordinary dataset, the repository record should make the situation obvious. Someone looking at the landing page should be able to tell whether the files are openly available, under an embargo, or subject to a request process.

Restricted data need particular attention because "available on request" is not much of a policy by itself. The project documentation should explain who handles requests and what information a requester needs to provide. If approval is required, identify the responsible role rather than leaving future users to guess which former team member might still answer an email.

There is another useful distinction, the data and the metadata do not necessarily disappear together. The FAIR principles explicitly call for metadata to remain accessible even when the underlying data are no longer available. A repository that can preserve a dataset's descriptive record after an embargo or withdrawal is therefore preferable to a storage arrangement in which the existence of the dataset disappears with the files.

## Making data interoperable

Interoperability is often misunderstood as "use CSV." CSV can be an excellent format for tabular data, but it is not automatically the right format for every dataset.

The better rule is to choose a format that is documented, widely supported, and appropriate for the structure of the data. A simple table might work well as CSV. Structured records might be better represented as JSON. Scientific datasets with multidimensional arrays or time-series data may have field-specific formats such as NetCDF. Image, audio, geospatial, and other data types have their own established conventions.

The same principle applies to terminology. If a research community has a controlled vocabulary or ontology, using its terms makes it easier for another system to interpret the data consistently. A molecular-biology project, for example, may use established ontology terms rather than inventing local names for concepts that already have community identifiers.

Some information should never be left implicit. Record units rather than assuming that another researcher will know whether a measurement is in metres or centimetres. Record coordinate reference systems for spatial data and time zones or time conventions for temporal data. These details can look obvious when a project is active and become surprisingly difficult to reconstruct a few years later.

## Making data reusable

A reusable dataset needs more than a download button. Someone who was not present when the data were collected should be able to understand what the files represent, what was done to them, and what they are permitted to do with them.

Licensing is part of that. Where legally and ethically appropriate, use a clear reuse license or rights statement. CC0 and CC BY are common examples, but they are not interchangeable and are not suitable for every type of data. Personal or otherwise restricted data may require a different approach. Intellectual-property restrictions, consent agreements, institutional policies, and funder requirements should be considered before applying a license.

Provenance is equally important. Record how the data were collected and transformed. For experimental data, this may include the instrument and relevant settings. For survey data, it may include the questionnaire and coding decisions. For computational work, it should include the processing steps used to produce derived files.

Do not hide known problems. If observations were excluded, measurements failed quality control, variables were changed, or a particular subset should not be interpreted in the same way as the rest, document it. A future researcher should not have to reconstruct the project's history from scattered conversations and filenames.

## Metadata that survives the project

Metadata is the information that explains what a dataset is and how it should be interpreted. It should not exist only in the memory of the person who collected the data.

For a typical dataset, the documentation should identify its title and creators, the period and scope of collection, the methods or instruments used, relevant calibration information, the meaning and units of variables, processing history, and applicable access or reuse restrictions. A data dictionary is particularly useful for tabular data because it gives a future user a direct mapping between a variable name and its meaning.

A small team does not need to invent its own metadata system. Where a mature community standard exists, use it. Examples include the Ecological Metadata Language (EML) in ecology, the Data Documentation Initiative (DDI) in social science, and Climate and Forecast (CF) conventions for many climate and earth-science datasets. Dublin Core and DataCite provide broader metadata structures, although they serve somewhat different purposes from field-specific standards.

The important point is not to choose the standard with the longest specification. It is to use a structure that another researcher or repository can understand without needing a private explanation from the original team.

For a simple tabular project, a machine-readable data dictionary might be a CSV or TSV file stored alongside the dataset. For other disciplines, a field-specific metadata format may be more appropriate. A Word document can still be useful for narrative documentation, but it should not be the only place where essential machine-readable information exists.

## File names that remain understandable

File naming is one of those small decisions that becomes expensive when nobody makes it consistently.

A useful convention is short enough that researchers will actually follow it. Dates can be written as `YYYY-MM-DD` or `YYYYMMDD`, followed by a project or site identifier and a meaningful description of the file. A version number is useful when the file represents a distinct revision.

For example:

```text
2024-03-15_site3_temperature_raw_v1.csv
```

This tells a future reader considerably more than:

```text
data (2) FINAL final2.csv
```

Spaces are not inherently invalid, but avoiding them reduces friction when files are used in command-line tools, scripts, URLs, and automated workflows. Similarly, avoid characters that are reserved or troublesome on common operating systems and tools, particularly `/`, `\`, `:`, `*`, and `?`.

The goal is not to create a complicated naming grammar. It is to make filenames useful when a file is separated from the folder where it was originally stored.

## Choosing a repository

There is no single FAIR repository for every research group.

A general-purpose repository can be a reasonable choice when the research community does not have a suitable disciplinary repository. Zenodo, Dryad, and Figshare are examples of services used for research outputs, although their policies, limits, and features differ and should be checked before a project commits to one.

A disciplinary repository may be preferable when one exists. Genomic sequence data, for example, normally have established repositories such as GenBank and the Sequence Read Archive. PANGAEA is widely used for earth and environmental science data, while ICPSR provides infrastructure for many social-science datasets.

The repository should be selected based on the actual data and the project's requirements, not simply because it is familiar. Check whether it accepts the file types and volume you need, assigns persistent identifiers, supports the required access controls, provides adequate metadata, has an appropriate preservation policy, and satisfies any journal or funder requirements.

re3data is useful when you do not know which repository is appropriate. It provides a searchable registry of research data repositories and their characteristics.

Before depositing a dataset, it is also useful to calculate a checksum for important files. SHA-256 is a reasonable general-purpose choice. MD5 may still appear in older workflows, but it should not be treated as equivalent to SHA-256 for security-sensitive integrity checks. A checksum helps detect whether a downloaded or transferred file has changed; it does not by itself prove where the file came from.

## Reproducible code and software environments

A script that worked on one computer two years ago may fail on another machine because a package, interpreter, operating-system library, or other dependency has changed.

The simplest useful record is an environment file kept with the analysis code. In a Python project, for example:

```bash
pip freeze > requirements.txt
```

The resulting file can be used with:

```bash
pip install -r requirements.txt
```

For a Conda environment:

```bash
conda env export > environment.yml
```

and later:

```bash
conda env create -f environment.yml
```

These files are useful, but neither should be mistaken for a perfect description of the entire computational environment. `pip freeze` records the installed Python packages and versions; a Conda export can contain platform-specific information and may need adjustment when recreated elsewhere.

For projects where the software environment itself is important to reproducibility, a container can provide a more controlled environment. A minimal Dockerfile might look like this:

```dockerfile
FROM python:3.11-slim

COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . /project
WORKDIR /project
```

Containers help package software dependencies and system components together, but they do not reproduce everything about the original machine. Hardware, external services, data sources, host-kernel behavior, and other factors can still affect a computation.

On shared research-computing systems, Apptainer is commonly used where Docker's requirements are unsuitable.

## Write the README before you forget the project

A README is often the most useful document in a research repository because it gives a new person a starting point.

It does not need to be long. It needs to answer the questions that someone unfamiliar with the project will have: What is this? What files are here? Where is the metadata? How is the software environment created? How is the analysis run? What license or access conditions apply? How should the work be cited? Who should be contacted if something is unclear?

A small project can start with something like this:

```markdown
# <Project title>

## Description

<One paragraph explaining what the dataset or code contains
and why it exists.>

## Directory structure

<Explain the important top-level folders and files.>

## Data dictionary

<Identify the metadata or data-dictionary file.>

## Environment setup

<Commands needed to recreate the software environment.>

## Usage

<Commands or instructions for reproducing the main analysis.>

## License and citation

<License or access conditions and the preferred citation.>

## Contact

<Name or project role and contact method.>
```

The README should be updated when the project changes. A README that describes a project accurately at publication but becomes wrong six months later is not much better than having no README.

## Version control: Git for the parts that belong in Git

Git is useful for code, documentation, configuration files, and other relatively small text-based files. It is not a good place to put multi-gigabyte imaging datasets or other large binary research data simply because the project happens to use Git.

For large datasets, keep the data in an appropriate storage or repository and put the scripts, documentation, and references needed to work with that data under version control.

A researcher who has never used Git can start with five commands:

```bash
git init
git add <file>
git commit -m "Describe the change"
git log
git diff <file>
```

`git init` creates the repository. `git add` stages changes for the next commit, and `git commit` records a snapshot. `git log` shows the history, while `git diff` makes changes visible instead of leaving them implicit.

A small research group does not need a complicated branching strategy. A main branch and clear commit messages may be enough for routine work. Experimental analyses that may never become part of the final study can be isolated in branches when necessary.

At an important project milestone, such as submission of a paper, create a version tag:

```bash
git tag v1.0
```

The point is to identify the exact state of the code associated with that version of the research. If the project later changes, the tagged version remains a reference to what was actually used at that point.

GitHub or GitLab can provide remote hosting and collaboration, but they should not automatically become the archival location for the research dataset itself.

## Avoiding the single-person problem

Small research groups have a predictable weakness: one person often knows how everything works.

The informal term *bus factor* is sometimes used to describe this problem. A project with a bus factor of one depends critically on one person's knowledge. If that person leaves, becomes unavailable, or simply forgets how an old analysis worked, the rest of the group may have the files without having the knowledge required to use them.

The practical response is documentation and shared responsibility.

Assign someone responsibility for keeping the dataset documentation current. Make the README and data dictionary part of the dataset rather than optional paperwork. Keep project documentation and processing scripts in shared, access-controlled storage rather than on one person's computer.

Credentials are different: passwords, API keys, tokens, and other secrets should not be placed in Git repositories, README files, or ordinary shared documents. Use the institution's approved password manager or secret-management system instead.

When a researcher who holds important project knowledge is leaving, a short handover session can be more valuable than another page of general documentation. Walk through the data, processing steps, repository, software environment, and unresolved problems while the person who knows the history is still available to answer questions.

## FAIR project checklist

The list below is intentionally shorter than the guide. Its purpose is to identify gaps at project milestones, not to replace the documentation.

### Findable

- The dataset has a persistent identifier or a documented plan for obtaining one.
- The title and description contain useful search terms.
- Contributors are identified consistently, using persistent identifiers such as ORCID where appropriate.
- The dataset is deposited or indexed in an appropriate repository.

### Accessible

- The repository record states how the data can be accessed.
- Restrictions, embargoes, or request procedures are documented.
- The dataset's metadata will remain available even if the files themselves become unavailable.

### Interoperable

- File formats are appropriate, documented, and supported by the research community where possible.
- Units, coordinate systems, time conventions, and other assumptions are explicit.
- Established vocabularies, ontologies, or metadata standards are used where they are appropriate.

### Reusable

- The rights or license conditions are clear.
- A data dictionary or equivalent documentation explains the variables and their meanings.
- Collection and processing history is documented.
- Known exclusions, limitations, and quality issues are recorded.
- The software environment is documented when code is required to interpret or reproduce the results.
- A README explains how the dataset or code is organized and used.
- Someone is responsible for maintaining the documentation.

## Sources and version notes

This guide is based on the FAIR Guiding Principles described by Wilkinson et al. (2016), together with current guidance from NSF, NIH, repository infrastructure, and common research-data practices.

The FAIR principles themselves do not prescribe particular technologies such as DOIs, Git, CSV, Docker, or any specific repository. Those are implementation choices. The recommendations in this guide therefore distinguish between what the FAIR principles require conceptually and what is practical for a small research group.

For current grant requirements, consult the relevant funder's documentation rather than relying on this guide. In particular, NIH's 2026 Data Management and Sharing Plan format applies to applications with due dates on or after May 25, 2026, and NSF's requirements are governed by its current Proposal & Award Policies & Procedures Guide and applicable solicitation. Requirements can change independently of the FAIR principles.

This is a documentation-based guide rather than a report of independent testing of every repository, command, or software configuration described here. Repository features, storage limits, interfaces, and funder requirements should be checked against their current documentation before being adopted for a live project.

### Key references

Wilkinson, M. D., Dumontier, M., Aalbersberg, I. J., et al. (2016). *The FAIR Guiding Principles for scientific data management and stewardship*. Scientific Data, 3, 160018. doi:10.1038/sdata.2016.18

National Science Foundation. *Preparing Your Data Management and Sharing Plan*. Current NSF guidance.

National Institutes of Health. *Writing a Data Management and Sharing Plan*. Current NIH guidance.

re3data.org. *Registry of Research Data Repositories*.

Zenodo. *GitHub integration documentation*.
