# Meta KG API

Meta KG API enables users to query the CZI-Meta Knowledge Graph (KG) stored in a graph database. The KG contains bibliographic information for biomedical research output (referred to as 'works') such as title, abstract, journal or repository name, author, keywords, citation data etc. A broad range of research outputs is represented in the KG, including journal articles, preprints, datasets, protocols, software, conference proceedings and clinical trial reports.

It is an HTTP read-only API. 

## Common Operations

Each API endpoint supports four basic operations. 

### Filtering

Filtering is for exact field matching, e.g. give me all documents from a certain date.

### Text Queries

When an exact field match is limiting your results too much, you may
want to use a text query. A text query will look for specific words 
within specific fields, without having to match that field exactly. For
example, if you're looking for all works by a given contributor, but you
know they have published under two similar names, this is a good option.

### Pagination

Pagination is for loading different pages of the results. The default number
of results per page is 20.

### Sorting

You can sort the by some, but not all fields, of the records.

## API Resources

The API has the following resources:

* [Work](works.md)
* [Person](persons.md)
