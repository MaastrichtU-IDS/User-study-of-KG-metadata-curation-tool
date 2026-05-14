# User-study-of-KG-metadata-curation-tool

This repository shares all the resources used in the manuscript "AI Assisted Knowledge Graph Metadata Curation: A User Study". This study propose a form-based, AI-assisted tool to facilitate the KG metadata authoring. 
This approach exposes the fields defined in a recently proposed KG metadata specification in a form structure. Suggestions are generated for each metadata element through LLM-based retrieval augmented generation from user-provided documentation, while conforming  to the specification's required structure and value formats. Users can inspect, accept, or reject these suggestions before finalizing the metadata, thereby combining automation support with user control.

Here you can find the KG documentations, User study Form, user study questionnaires responses, submitted metadata by participants (tasks outputs), KG metadata spreadsheet, analysis scripts, and supplementary Excel files. The source code for the tools can be found at: https://github.com/MaastrichtU-IDS/knowledge-graph-metadata-form.


You can access tools at the following:

The AI-assisted form: https://maastrichtu-ids.github.io/knowledge-graph-metadata-form/?mode=llm

Standard form:  https://maastrichtu-ids.github.io/knowledge-graph-metadata-form/?mode=regular

 Turtle editor: https://maastrichtu-ids.github.io/knowledge-graph-metadata-form/?mode=turtle 
 
```

To reproduce the analysis results run Scripts/User_study_Analysis.ipynb.

```

## Metadata Specification

Below is a sample of five fields from the metadata specification, showing how each element is defined, its expected data type, its purpose, and an example from Wikidata.

You can access the full KG metadata specification [here on Google Sheets](https://docs.google.com/spreadsheets/d/1pC6Hj6wl-uzyFeBmK19f_UaQyuUN4-DQ/edit?gid=945024402#gid=945024402).


<h3>Metadata Specification (Excerpt)</h3>

<table style="width:80%; font-size:88%; margin:auto; border-collapse:collapse;">
<thead>
<tr>
<th style="border-bottom:1px solid #ccc; padding:6px;">Field</th>
<th style="border-bottom:1px solid #ccc; padding:6px;">Value Specification</th>
<th style="border-bottom:1px solid #ccc; padding:6px;">Purpose / Use</th>
<th style="border-bottom:1px solid #ccc; padding:6px;">Wikidata Metadata Example</th>
</tr>
</thead>
<tbody>
<tr>
<td style="padding:6px;"><b>Identifier</b></td>
<td style="padding:6px;"><code>rdfs:Literal</code> or <code>IRI</code></td>
<td style="padding:6px;">A unique identifier for the dataset.</td>
<td style="padding:6px;"><code>wd:Q2013</code></td>
</tr>
<tr>
<td style="padding:6px;"><b>Title</b></td>
<td style="padding:6px;"><code>rdf:LangString</code> or <code>xsd:string</code></td>
<td style="padding:6px;">The main name of the dataset or knowledge graph.</td>
<td style="padding:6px;"><code>"Wikidata Knowledge Base"</code></td>
</tr>
<tr>
<td style="padding:6px;"><b>Description</b></td>
<td style="padding:6px;"><code>rdf:LangString</code> or <code>xsd:string</code></td>
<td style="padding:6px;">Provides a short explanation of the dataset content and scope.</td>
<td style="padding:6px;"><code>"A free and open knowledge base that can be read and edited by humans and machines."</code></td>
</tr>
<tr>
<td style="padding:6px;"><b>Theme / Category</b></td>
<td style="padding:6px;"><code>IRI</code></td>
<td style="padding:6px;">Specifies the topical area or classification of the dataset.</td>
<td style="padding:6px;"><code>&lt;http://www.wikidata.org/entity/Q21198&gt;</code> (Ontology)</td>
</tr>
<tr>
<td style="padding:6px;"><b>Distribution Information</b></td>
<td style="padding:6px;">
  <code>dcat:Distribution</code><br>
  (includes sub-elements:<br>
  &nbsp;&nbsp;<i>title</i><br>
  &nbsp;&nbsp;<i>description</i><br>
  &nbsp;&nbsp;<i>mediaType</i><br>
  &nbsp;&nbsp;<i>downloadURL</i><br>
  &nbsp;&nbsp;<i>accessURL</i>)
</td>
<td style="padding:6px;">Describes how and where the dataset is made available.</td>
<td style="padding:6px;">
  title: “Wikidata dump files”;<br>
  mediaType: “application/gzip”;<br>
  downloadURL: 
  <a href="https://dumps.wikimedia.org/wikidatawiki/entities/">
    https://dumps.wikimedia.org/wikidatawiki/entities/
  </a>
</td>
</tr>
</tbody>
</table>

---

*Note:* The schema specifies which elements are **required** and which are **optional**, and defines the **expected value type** for each.  
For instance, a title is free text, a theme is an IRI, a date follows a standard date format, and a distribution includes structured subfields like *mediaType*, *downloadURL*, and *accessURL*.

*Note:* The “optional” and “required” indicators on this form apply only to the final version of the tool. For the purposes of this user study, please disregard them and complete as many fields as you are able to.

Structural relationships between elements of specification is shown below:

<p align="center">
  <img src="participants%20letter/S-rel3.png" alt="Structural relationships between components of specification ." width="900"/>
</p>

### Tool A – Turtle Editor

This tool provides a **text editor** with Turtle syntax validation.  
Here, you can manually create the metadata in Turtle format.

**Steps:**
1. Skim the KG documentation to understand what it describes.  
2. Open the metadata schema checklist and note which elements you must include.  
3. Gather exact values, such as IRIs for themes, sources, and linked resources when available.  
4. Map each element from the schema to a simple Turtle statement, keeping the format short and consistent.  
5. Use the editor’s validation to check that your Turtle is syntactically correct.

*Example screenshot of Tool 1:*
<p align="center">
  <img src="participants%20letter/text_editor.png" alt="Turtle Editor " width="700"/>
</p>

---

### Tool B – Form Interface

In this tool, you can describe a KG using a **web form**.  
You do not need to write any Turtle syntax — the form automatically converts your answers into structered format.

**Steps:**
1. Skim the KG documentation.  
2. Fill in the field values according to the metadata specification.  

*Example screenshot of Tool 2:*
<p align="center">
  <img src="participants%20letter/form.png" alt="form " width="700"/>
</p>


---

### Tool C – AI Assisted Form

The third tool uses **AI assistance** to help you fill the metadata form.  
You must upload the natural-language KG document, and the tool will generate **AI suggestions** for each metadata field.

**Steps:**
1. Upload the KG documentation.  
2. Click on each metadata field to view the AI suggestions.  
3. Review the suggestions, and if you accept the sugesstion add them. If you dont accept some of the suggesstions you can reject them. 

*Example screenshot of Tool 3:*
<p align="center">
  <img src="participants%20letter/llm.png" alt="AI-Assisted Form" width="700"/>
</p>


---
