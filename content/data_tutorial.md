---
title: Data Tutorial
language: en
slug: data_tutorial
---

<h2>Contents:</h2>
<a href="#Generating a template">Generating a template</a> <br>
<a href="#Uploading and validating data">Uploading and validating data</a> <br>
<a href="#Requesting trait terms">Requesting trait terms</a> <br>

<h3 id="Generating a template">Generating a template</h3>

1. Go to <a href="geome-db.org/about">GEOME</a> and create an account
2. Create a project and join the FuTRES Team
3. Select the template generator to create a spreadsheet for entering data
  * Select terms
  * Export to a spreadsheet application
    + Speadsheet has:
      - Instructions
      - Template (required field in red)
      - Controlled vocabulary
      - Definition for attributes

<h3 id="Uploading and validating data"> Uploading and validating data</h3>

1. Upload to GEOME under your project in FuTRES Team
  * Can load multiple spreadsheets at one time under same expedition name
  * Will give an error if a value in a field is wrong (e.g., a string where numbers should be)
2. Name your project:
  * Each project has its own abstract
  * FuTRES_taxon_contributor_locality_time/period
3. Name your expedition:
  * FuTRES_taxon_contributor_locality_time.period and version number or date

<h3 id="Requesting trait terms">Requesting trait terms</h3>

1. Check that the term is not currently there
  - go to GEOME -> FuTRES Template -> measurementType DEF
2. Go to <a href="https://github.com/futres/fovt">FuTRES Ontology of Vertebrate Traits (FOVT)</a>
3. Create a <a href="https://github.com/futres/fovt-data-pipeline/issues/new">New issue</a>
  * Needs:
    + anatomical feature
    + anatomical points and/or anatomical axis
    + measurement (e.g., width, length, etc.)
    + reference for measurement (illustration if have it)
