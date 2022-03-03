---
title: How It Works
language: en
slug: how_it_works
---
<p>The purpose of FuTRES is to make trait data from biological and paleontological specimens accessible in a format that improves discoverability and promotes novel research. By following a few steps and using new tools developed by the FuTRES team, these data can be shared on the FuTRES platform, which is backed by an ontological framework that enables logical reasoning. Here is a <a href="https://youtu.be/r2LNKU9hQEE">quick introduction to FuTRES</a>.</p>

<p>FuTRES data is available to all. If you do not want your data shared and in FuTRES immediately, data providers can still create a project and upload it to GEOME and set their project or expedition as "private" so that it will not be ingested to FuTRES; change to "public" when ready and the dataset (expeditions) will be findable in the FuTRES datastore. All data is assumed to be CC0 licensing, unless otherwise specified as CCBY or BSD.</p>.

<p><figure><img src="/media/FuTRESworkflow.png"/></figure></p>

<h1><img src="/media/templateIcon.png"
width="100"
style="float:left;">

## Step 1: Template 

<p>We have developed a template (<a href="https://github.com/futres/template">viewable here</a>) to help data providers create datasets that are ready for ingestion into the FuTRES knowledge base. The field names in the template largely correspond to <a href="https://dwc.tdwg.org/">Darwin Core</a> terms. Since Darwin Core is the most commonly used standard for sharing biodiversity occurrence data, these fields may already be pre-existing in most collections databases, or if not, they can be easily mapped or crosswalked from other existing fields.</p>

### Existing Data and Future Collaborations 
<p>Currently, the FuTRES team is working with <a href="https://futres.org/team/">Principal Investigators</a>, Dr. Kitty Emery, Dr. Ray Bernor, and Dr. Edward Davis, to share existing zooarchaeological and paleontological specimen datasets with associated trait information. These use cases have informed the development of the FuTRES template and the <a href="https://github.com/futres/fovt">FuTRES Ontology of Vertebrate Traits</a>. However, we are hosting community <a href="https://futres.org/workshop/">workshops</a> and are happy to receive feedback and additional trait-focused datasets from other sources.<br>
  You can <a href="https://github.com/futres/fovt-data-pipeline/issues/new">request trait terms</a> and see <a href="https://geome-db.org/workbench/template">existing trait terms</a>. We have also developed a <a href="https://futres.org/data_tutorial/">tutorial</a> for adding data and traits.</p>

<h1><img src="/media/ontologyIcon.png"
width="100"
style="float:left;">
  
## Step 2: Ontology

<p> The data model relies heavily on the <a href="https://obofoundry.org/ontology/bco.html">Biological Collections Ontology</a>. This maps classes and data properties in the template to the trait terms and aids in reasoning (step 4).</p>

<p>The <a href="https://github.com/futres/fovt">FuTRES Ontology of Vertebrate Traits</a> (FOVT) is a fundamental tool to accomplish the FuTRES project goals. An ontology is a knowledge representation which describes concepts and their relationships to one another in a logical framework that is understandable by machines and humans. This logical format allows the data points in an ontology knowledge base to be reasoned over, allowing new inferences to be gained. The FOVT is an application ontology specifically designed to serve the purposes of the FuTRES projects. It was developed by Dr. Ramona Walls, Dr. Meghan Balk, and Laura Brenskelle, and it reuses many existing ontologies (for example, <a href="https://www.ebi.ac.uk/ols/ontologies/uberon">UBERON</a>, <a href="http://www.obofoundry.org/ontology/pato.html">PATO</a>, and <a href="http://www.obofoundry.org/ontology/bspo.html">BSPO</a>) to conceptualize different vertebrate traits. These become the controlleed vocabulary for the templte term "measurementType".</p>

## Step 3: Data Model
  
<p>The FuTRES data model provides each row as a measurement (long format). This differs from how researchers may normally collect data, where each row is a specimen. Having each row as a measurement makes it easier for the pipeline as well as for subsequent analyses. Each measurement has a unique diagnosticID. These diagnosticIDs are connected to each other via materialSampleID or groupingID. The materialSampleIDs are unique to each specimen. The materialSampleIDs are grouped by individualID, which are unique for each organism. As an example, a dataset with four measurements, two from the illium and two from the femur all belonging to the individual animal would look like this:</p>

| individualID | materialSampleID | catalogNumber | diagnosticID | scientificName | measurementType | measurementValue | measurementUnit|
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
|1|1|FMNH PR2081|1|<i>Tyrannosaurus rex</i>|illium length|1525|mm|
|1|1|FMNH PR2081|2|<i>Tyrannosaurus rex</i>|illium depth|608|mm|
|1|2|FMNH PR2081|3|<i>Tyrannosaurus rex</i>|femur length|1321|mm|
|1|2|FMNH PR2081|4|<i>Tyrannosaurus rex</i>|femur circumference|580|mm|

<h1><img src="/media/pipelineIcon.png"
width="100"
style="float:left;">

## Step 4: Pipeline 

<p>The data processing pipeline is comprised of five main steps: pre-processing, triplifying, reasoning, conversion to a tabular format, and data loading. The pipeline is dependent on an existing ontology that defines and relates the terminology used in the data, but does not require a specific structure. For more information, you can watch this short video on the <a <strong>FOVT Data Pipeline</strong></a>.</p>

<p>The pre-processing step lets users write a custom conversion method for each dataset into a common format (while the template helps to minimize the amount of customization needed). After pre-processing, RDF triples are generated by reading configuration files from each data source that includes term mappings, data validation, and creating relationships between processes and objects as defined by the ontology. All triples are referenced by globally unique identifiers by appending record identifiers from the input data to globally unique, resolvable HTTP prefixes that can be customized for each project. Because instance identifiers are derived from the input data, output identifiers can be linked back to the specific records in the raw source data, which also provides a mechanism to track data provenance.</p>

<p>The next step in the workflow - reasoning - uses the bundled <a href="https://github.com/INCATools/ontology-development-kit">Ontology Development Kit</a> that supports multiple description logic profiles through multiple reasoners. The workflow provides an optional configuration file to OntoPilot that further allows users to customize the reasoning process. The reasoning helps with more flexible searches; for example, searching for "length" will provide all the length terms from the ontology that are in the FuTRES datastore.</p>

<p>The reformatting workflow converts the data to a series of CSV files via a customizable SPARQL query through <a href="https://github.com/biocodellc/query_fetcher">query_fetcher</a>, a bundled package for fast conversion of RDF to tabular data that is built upon the <a href="https://jena.apache.org/index.html">Apache Jena Java Library</a>. The output data can be loaded into whatever data storage system the user prefers, including key/value stores (e.g., ElasticSearch), relational databases (e.g., PostgreSQL), or triplestores (e.g., Blazegraph).
