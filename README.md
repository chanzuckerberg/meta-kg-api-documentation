## The Meta API is currently in pilot phase. Please contact us if you are interested in trying it out.

# Meta API
The Meta API enables users to query the Meta knowledge graph. The graph database contains bibliographic information for biomedical research output (referred to as 'works') such as title, abstract, journal or repository name, author, keywords, references, etc. A broad range of research outputs is represented in the knowledge graph including journal articles, preprints, datasets, protocols, software, conference proceedings and clinical trial reports.

The Meta API is HTTP read-only. 

## Common Operations
Each API endpoint supports four basic operations. 

### Filtering
Filtering is for exact field matching, e.g. give me all documents from a certain date.

### Text Queries
When an exact field match is limiting your results too much, you may want to use a text query. A text query will look for specific words 
within specific fields, without having to match that field exactly. For example, if you're looking for all works by a given contributor, but you
know they have published under two similar names, this is a good option.

### Pagination
The default number of results per page is 500. Pagination enables loading subsequent pages of results to return the full query as the max is exceeded.

### Sorting
Sorting is available for some, but not all fields, of the records. See details in the documentation pages for Works and Person resources.

## API Resources
The API has the following resources:
* [Work](works.md)
* [Person](persons.md)

To visualize and interact with the API resources, visit the Meta API's [Swagger docs](https://meta-api-docs.prod.meta-infra.org/).

## About Meta
Meta is a technology project at the Chan Zuckerberg Initiative (CZI). CZI Science's mission is to support the science and technology that will make it possible to cure, manage, or prevent all diseases. Meta is an open, comprehensive knowledge-graph discovery system to enable scientists, physicians, students, patients, and the scientific community to navigate the corpus of biomedical and scientific information. By mapping science as it happens, Meta's mission is to make it possible for researchers to look beyond their field of expertise, generate new hypotheses, understand connections and context, and thus accelerate the process of science as a whole. 

## Reporting Security Issues
If you believe you have found a security issue, please responsibly disclose by contacting us at security@chanzuckerberg.com.”

