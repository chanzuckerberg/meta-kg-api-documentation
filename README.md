## The Meta API is currently in pilot phase. Please contact us if you are interested in trying it out.

# Meta API
Meta is a technology project at the Chan Zuckerberg Initiative (CZI). CZI Science's mission is to support the science and technology that will make it possible to cure, manage, or prevent all diseases. Meta is an open, comprehensive knowledge-graph discovery system to enable scientists, physicians, students, patients, and the scientific community to navigate the corpus of biomedical and scientific information. By mapping science as it happens, Meta's mission is to make it possible for researchers to look beyond their field of expertise, generate new hypotheses, understand connections and context, and thus accelerate the process of science as a whole. 

The Meta API enables users to query the Meta knowledge graph. The graph database contains bibliographic information for biomedical research output (referred to as 'works') such as title, abstract, journal or repository name, author, keywords, references, etc. A broad range of research outputs is represented in the knowledge graph including journal articles, preprints, datasets, protocols, software, conference proceedings and clinical trial reports.

__The Meta API is HTTP read-only.__

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

## Issues & Feature Requests
We welcome feedback on the API. Please report any system issues or request features by creating an [issue in this repository](https://github.com/chanzuckerberg/meta-kg-api-documentation/issues).
__If you believe you have found a security issue, please responsibly disclose by contacting us at security@chanzuckerberg.com.__

## License 
### API data
All data from the API are available through the CC-0 license waiver.

### API documentation 
Permission is hereby granted, without written agreement and without
license or royalty fees, to use, copy, modify, and distribute this
software and its documentation for any purpose, provided that the
above copyright notice and the following two paragraphs appear in
all copies of this software.

IN NO EVENT SHALL THE COPYRIGHT HOLDER BE LIABLE TO ANY PARTY FOR
DIRECT, INDIRECT, SPECIAL, INCIDENTAL, OR CONSEQUENTIAL DAMAGES
ARISING OUT OF THE USE OF THIS SOFTWARE AND ITS DOCUMENTATION, EVEN
IF THE COPYRIGHT HOLDER HAS BEEN ADVISED OF THE POSSIBILITY OF SUCH
DAMAGE.

THE COPYRIGHT HOLDER SPECIFICALLY DISCLAIMS ANY WARRANTIES, INCLUDING,
BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND
FITNESS FOR A PARTICULAR PURPOSE.  THE SOFTWARE PROVIDED HEREUNDER IS
ON AN "AS IS" BASIS, AND THE COPYRIGHT HOLDER HAS NO OBLIGATION TO
PROVIDE MAINTENANCE, SUPPORT, UPDATES, ENHANCEMENTS, OR MODIFICATIONS.
