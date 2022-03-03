---
title: Data Tutorial
language: en
slug: data_tutorial
---
We ask researchers wishing to contribute data to FuTRES to use the following procedure to provide data.  

<h2>Contents:</h2>
<b><a href="#Generating a template">Generating a template</a></b> <br>
<b><a href="#Uploading and validating data">Uploading and validating data</a></b> <br>
<b><a href="#Requesting trait terms">Requesting trait terms</a></b> <br>

<a href="https://www.youtube.com/watch?v=WyJKmFsUVKc"><strong>Video on Loading Data into GEOME (video)</strong></a>

<h3 id="Generating a template">Generating a template</h3>

1. Go to <a href="https://geome-db.org/about">GEOME</a> and create an account
2. Create a project and join the FuTRES Team
    * Naming convention: FuTRES_taxon_contributor_locality_time.period
    * It is up to the user to choose projects / expeditions (datasets) as necessary
        + e.g., each expedition could be a site and each project a collection
3. Fill in project metadata
    * project title
    * project description
    * visibility (public/private)
       + Note that even if projects are public, expeditions can be private
    * principle investigator
    * principle investigator affiliation
    * citation
4. Select the template generator to create a spreadsheet for entering data
    * Select terms
    * Export to a spreadsheet application
        + Speadsheet has:
            - Instructions
            - Template (required field in red)
            - Controlled vocabulary
            - Definition for attributes
     * Determine organization of expedition (datasets) however you would like (e.g., site). FuTRES API already searches based on taxonomy and measurement.
5. Fill in expedition (dataset) metadata
     * expedition title
         + Naming convention: FuTRES_taxon_contributor_locality_time.period_version number or date
     * expedition code
     * if expedition can be public or private

<h3 id="Uploading and validating data"> Uploading and validating data</h3>

1. Upload to GEOME under your project in FuTRES Team Project
  * Can load multiple spreadsheets at one time under same expedition name
  * Will give a warning if something is wrong, but not fatal (can ignore; use your discretion)
  * Will give an error if a value in a field is wrong (e.g., a string where numbers should be)
2. Fill in expedition metadata
      - expedition title
            - Naming convention: FuTRES_taxon_contributor_locality_time.period_version number or date
      - expedition code 
3. Name your expedition:
  * FuTRES_taxon_contributor_locality_time.period and version number or date

<h3 id="Requesting trait terms">Requesting trait terms</h3>

1. Check that the term is not currently there
  * Click on measurementType DEF of <a href="https://geome-db.org/workbench/template">template</a>
2. Go to <a href="https://github.com/futres/fovt">FuTRES Ontology of Vertebrate Traits (FOVT)</a>
3. Create a <a href="https://github.com/futres/fovt-data-pipeline/issues/new">New issue</a>
  * Needs:
    + term label
    + synonyms
    + Parts of the term
      - anatomical feature
      - anatomical points and/or anatomical axis
      - measurement (e.g., width, length, etc.)
    + reference for measurement (illustration if have it)
    + attribution (ORCID id)
