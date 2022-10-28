---
title: Data Tutorial
language: en
slug: data_tutorial
---

## Contributing Data to FuTRES

FuTRES is partnering with <a href="https://geome-db.org/">GEOME</a> to help users load and validate data. General instructions on using GEOME are available on the <a href="https://geome-db.org/about">GEOME Getting Started</a> and a short youtube video on <a href="https://www.youtube.com/watch?v=WyJKmFsUVKc&feature=youtu.be">Loading FuTRES data into GEOME</a>.

<h2>Contents:</h2>

<b><a href="#Generating a template">Generating a template</a></b> <br>
<b><a href="#Formatting data">Formatting data</a></b> <br>
<b><a href="#Uploading and validating data">Uploading and validating data</a></b> <br>
<b><a href="#Requesting trait terms">Requesting trait terms</a></b> <br>

<h3 id="Generating a template">Generating a template</h3>

1. Go to <a href="https://geome-db.org/about">GEOME</a> and create an account
2. Create a project and join the FuTRES Team
    * Project naming convention: FuTRES_taxon_contributor_locality_time.period
    * It is up to the user to choose projects / expeditions (datasets) as necessary
        + the organization of expeditions (datasets) can be however you would like (e.g., by site or time)
3. Fill in project metadata
    * project title
    * project description
    * visibility (public/private)
       + Note that even if projects are public, expeditions can be private
    * principle investigator
    * principle investigator affiliation
    * citation
       + This is needed if your license is CC BY or BSD 
4. Select the template generator
    * Required terms are automatically populated
    * Select any additional terms
    * Export to a spreadsheet application
        + Speadsheet has:
            - Instructions
            - Template (required field in red)
            - Controlled vocabulary
            - Definition for attributes
        + Note that licensing is assumed to be <a href="https://creativecommons.org/publicdomain/zero/1.0/legalcode">CC0</a>, unless specified as <a href="https://creativecommons.org/licenses/by/4.0/">CC BY</a> or <a href="https://opensource.org/licenses/BSD-3-Clause">BSD</a>
5. Fill in expedition (dataset) metadata
     * expedition title
         + Naming convention: FuTRES_taxon_contributor_locality_time.period_version number or date
     * expedition code
     * if expedition can be public or private

<h3 id="Formatting data">Formatting data</h3>

For the FuTRES datastore, data are expected to be in "long" format, where each row is a measurement. This means that there will be repeated data.

#### Formating

- All column headers use camelCase
- See the <a href="https://raw.githubusercontent.com/futres/template/910ecba9dd8159793a674de4fa5d582a40ebf8f7/template.csv">template</a> for suggested and required values under "example".
- All non-required columns need to be removed (not recommended) or moved into a "dynamicProperties" field (recommended)
- Three unique IDs are required:
    * diagnosticID
      + this is unique for every measurement (row)
      + this can be an index or a combination of index + catalog number + institutionID
    * materialSampleID
      + This is unique for every element (e.g., bone) and connects all the measurements on the same element
      + This can be a random indentifier or a combination of element + catalog number + institutionID
    * individualID
      + This is unique for ever individual and connects all the elements of an individual
      + This can be a random identifier or a combination of catalog number + institutionID

We have also created a <a href="
http://futres.shinyapps.io/pyConvApp">RShiny App</a>. Read the <a href="https://github.com/futres/RShinyFuTRES/blob/main/README.md">"readme" file</a> to learn the data formats we can use, dependencies needed, and limits of the app. Please send recommendations or issues to the <a href="https://github.com/futres/RShinyFuTRES/issues/new">RShiny FuTRES</a> repository.

<h3 id="Uploading and validating data"> Uploading and validating data</h3>

1. Upload to GEOME under your project in FuTRES Team Project
  * Can load multiple spreadsheets at one time under same expedition name
  * Will give a warning if something is wrong, but not fatal (can ignore; use your discretion)
  * Will give an error if a value in a field is wrong (e.g., a string where numbers should be)
2. Fill in expedition metadata
   * expedition title
      + Naming convention: FuTRES_taxon_contributor_locality_time.period_version number or date
   * expedition code 
3. Name your expedition:
  * FuTRES_taxon_contributor_locality_time.period and version number or date

<h3 id="Requesting trait terms">Requesting trait terms</h3>

1. Check that the term is not currently there
  * Click on measurementType DEF of <a href="https://geome-db.org/workbench/template">template</a>
  * Go to the <a href="https://www.ebi.ac.uk/ols/index">Ontology Lookup Service</a> to look for the term, restricting searches to only include "FOVT"
2. IF the term does not yet exist, go to <a href="https://github.com/futres/fovt">FuTRES Ontology of Vertebrate Traits (FOVT)</a> and create a <a href="https://github.com/futres/fovt-data-pipeline/issues/new">New issue</a>
  * Needs:
    + term label
    + synonyms
    + Parts of the term
      - anatomical feature
      - anatomical points and/or anatomical axis
      - measurement (e.g., width, length, etc.)
    + reference for measurement (illustration if have it)
    + attribution (ORCID id)
