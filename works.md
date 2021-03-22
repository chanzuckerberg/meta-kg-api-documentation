# Meta KG API - Works

The works API endpoint is for gathering information about the relationship between
a work, or many works, and other information in the graph.


## Work Response Shape

##### Work fields

|field name|data type| notes|
|----------|---------|------|
|id|string||
|czi_kg|integer||
|id|string||
|doi|string||
|type|string|work types are listed below|
|title|string|The title of the work|
|abstract|string|The abstract of the work|
|publicationDate|string||
|studyPhase|array|only applicable for type: ClinicalTrial. Values will be 'Phase 1', 'Phase 2', etc., or "Not Applicable"|
|studyType|string|only applicable for type: ClinicalTrial. Values are `Interventional` and `Observational`|
|subject|array||
|url|string||
|contributors|array|A listing of contributors to the work|
|reference|array||
|relation|array||
|keywords|array|A listing of keywords associated to the work|

##### Example

A single work will have a shape in the form:

```
 {
            "id": "URI",
            "identifiers": {
                "czi_kg": CZI_ID,
                "id": "URI",
                "pmid": "PMID",
                "doi": "DIO"
            },
            "type": "JournalArticle",
            "title": "Work Title",
            "abstract": "the abstract of the work",
            "publicationDate": "Date",
            "url": "URL",
            "contributors": [
                {
                    "id": "http://meta.org/kg/publication/Person/1214535",
                    "identifiers": {
                        "czi_kg": CZI_ID,
                        "orc_id": "ORC_ID",
                        "id": "URI"
                    },
                    "name": "Author Name",
                    "authorIndex": 0
                }
            ],
            "references": [],
            "relation": [],
            "keywords": [
                {
                    "term": "Woman",
                    "identifiers": {
                        "czi_kg": CZI_ID,
                        "umls_cui": "CUI"
                    }
                }
            ]
        }
```

## Work Types

There are several types of work represented in the API. These are:

* JournalArticle
* Preprint
* Software
* Dataset
* ConferenceProceeding
* Protocol
* ClinicalTrial

## Accessing a single work

A single work can be accessed by using a [curie](https://en.wikipedia.org/wiki/CURIE) to look up
a work based on a curie, use the format: `WorkType:id`, `doi:id`, `nct:id` and the endpoint
`/work`.

##### Example

Return a work with a given nct identifier:

`https://meta-api.staging.meta-infra.org/work/nct:NCT_ID`

## Accessing Multiple Works

Multiple works can be accessed at the endpoint `/work`

##### Example

Return a list of works:

`https://meta-api.staging.meta-infra.org/work`

### Filtering Works Results

#### Filtering works by work type

Works can be filtered to limit the results to one of the works types listed above. This is
done by adding a filter parameter with the works type specified as a type filter, like this
`?filter=type:Datafile`

##### Example

Return a list of works, all with type `JournalArticle`:

`https://meta-api.staging.meta-infra.org/work?filter=type:JournalArticle`

#### Filtering Works By Exact Field Match

Filtering works will Works can be filtered on a number of fields, both on the work itself
and related records.

Filtering is done by adding a filter parameter to the url, followed by a comma delimited list
of filter keys and values, like this: `?filter=field1:value1,field2:value2` The fields that a work can be filtered on
are:

* `pmid`: filter by exact pmid match. 
* `doi`: filter by exact doi match.
* `meta`: filter by exact internal meta match. 
* `publicationDate`: filter by publication date.
* `abstract`: filter by exact abstract match.
* `nct`
* `studyPhase`
* `iri`

##### Examples:

Return a work with a specific PMID or meta kg id:

`https://meta-api.staging.meta-infra.org/work?filter=pmid:21125585`

`https://meta-api.staging.meta-infra.org/work?filter=meta:21125585`

Return a work with a given nct identifier:

`https://meta-api.staging.meta-infra.org/work?filter=nct:NCT01611792`

Return a list of works from a given date:

`https://meta-api.staging.meta-infra.org/work?filter=publicationDate:2019-09-24`

Return a list of works with a given title:

`https://meta-api.staging.meta-infra.org/work?filter=title:Study+of+bacteria`

#### Filtering works with a range of values

The default behaviour for filters is an exact match, but you can add a prefix to the
filter to specify a range. Note that this is most useful to use on the publicationDate
field. The following prefixes are supported:

* `to-` This will perform a less than or equal match.
* `from-` This will perform a greater than or equal match.
* `before-` This will perform a less than match.
* `after-` This will perform a greater than match.

Note that you can combine multiple range filters on the same field.

##### Examples:

Return a list of works after a given date:

`https://meta-api.staging.meta-infra.org/work?filter=after-publicationDate:2019-09-24`

Return a list of works between two dates:

`https://meta-api.staging.meta-infra.org/work?filter=after-publicationDate:2019-09-24,before-publicationDate:2020-09-24`

#### Filtering on exact field matches of relationships to the work

You can also specify a field you want to have an exact match with on a relationship of the work.
This can be done with the following fields:

* `person.name`: Example: `https://meta-api.staging.meta-infra.org/work?filter=person.name:Cristina Battaglia`
* `person.role`: Example: `https://meta-api.staging.meta-infra.org/work?filter=person.role:creator`
* `person.orcid`: Example: `https://meta-api.staging.meta-infra.org/work?filter=person.orcid:0000-0003-3025-9657`
* `journal.title`: Example: `https://meta-api.staging.meta-infra.org/work?filter=journal.title:AARN News Letter`
* `keyword.name`: Example: `https://meta-api.staging.meta-infra.org/work?filter=keyword.name:1-Carboxyglutamic Acid`
* `keyword.cui`: Example: `https://meta-api.staging.meta-infra.org/work?filter=keyword.cui:C0000096`
* `relation.pmid`: Example: `https://meta-api.staging.meta-infra.org/work?filter=relation.pmid:PMID`
* `relation.nct`: Example: `https://meta-api.staging.meta-infra.org/work?filter=relation.nct:NCT`
* `relation.doi`: Example: `https://meta-api.staging.meta-infra.org/work?filter=relation.doi:DOI`
* `relation.title`: Example: ``
* `reference.pmid`: Example: ``
* `reference.meta`: Example: ``
* `reference.nct`: Example: ``
* `reference.doi`: Example: ``
* `reference.title`: Example: ``

### Sorting Results

Results can be order by adding a `sort` parameter to the query string, with the value in the format
`field:direction` where direction is either `ASC` or `DESC`. Results can only be sorted by works properties.

##### Example

Sort results by descending publication date:

`https://meta-api.staging.meta-infra.org/work?sort=publicationDate:DESC`

### Pagination

The API by default returns 20 results per page. You can change this by setting the `limit` parameter, but the maximum
value for that is 20. 
 
You can go to different pages of the results
by adding a `rowStart` parameter to the query string. The default number of results per page
in the API is 20, so to access page 2, 3, 4, etc., you would specify `rowStart=20`,
`rowStart=40`, `rowStart=60`, and so on.

##### Example

To get page four of the results:

`https://meta-api.staging.meta-infra.org/work?rowStart=60`

### Text queries within works

Text queries are useful for when you are looking for terms within the text of a work (e.g. 
within the title or abstract of a work), without looking for an exact match. A more specific
example would be looking for any works that have a specific term in the title or abstract.

Note that text queries can not be combined. If you specify multiple text queries in your
query string, the first specified in this precedence is the one that will be performed:

* work fields
* person
* keywords

#### Querying the work

You can do a text query against title and abstract fields of works by adding a `query` parameter to
the query string.

##### Example

`https://meta-api.staging.meta-infra.org/work?query=Calcium+sensing`

#### Querying the people related to a work

You can do a text query against name field of the people associated with works by adding a `person` parameter to
the query string.

##### Example

`https://meta-api.staging.meta-infra.org/work?person=Jonas`

#### Querying the keywords related to a work

You can do a text query against name field of the keywords associated with works by adding a `keywords` parameter to
the query string.

##### Example

`https://meta-api.staging.meta-infra.org/work?keywords=space+walk`
