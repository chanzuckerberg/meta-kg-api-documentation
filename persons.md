# Meta API - Person

The person endpoint is for gathering information about the relationship between a person or many persons with related work information in the Meta knowledge graph.

## Person response shape

##### Person fields

|field name|data type| notes|
|----------|---------|------|
|czi_kg|integer||
|id|string||
|doi|string||
|name|string|work types are listed below|
|work|array|A listing of works the person contributed to|

##### Example


A person response from the api will have the data in this format:

```
{
    "id": "URI",
    "identifiers": {
        "czi_kg": CZI_ID,
        "orc_id": "ORC_ID",
        "id": "URI"
    },
    "name": "Person Name",
    "work": {
        "id": "WORK URI",
        "identifiers": {
            "czi_kg": CZI ID,
            "id": "WORK URI",
            "pmid": "PMID",
            "doi": "DOI"
        },
        "type": "JournalArticle",
        "title": "Title of work",
        "publicationDate": "work date"
    }
}
```

## Accessing a single person
A single person can be accessed with a [curie](https://en.wikipedia.org/wiki/CURIE). To look up a person based on a curie, use the format: `person.person:id` and the endpoint `/person`.

## Accessing multiple persons
Multiple persons can be accessed at the endpoint `/person`

##### Example
Return a list of persons:

`https://api.meta.org/person`

### Filtering person results

#### Filtering person by exact match
The person endpoint can be filtered on a number of fields, both on the person itself and related records.

Filtering is done by adding a filter parameter to the url, followed by a comma delimited list of filter keys and values, like this: `?filter=field1:value1,field2:value2`

Filters include the following:
* `name`
* `publicationDate`
* `organization.name`


##### Examples:
Return a list of persons with a given name:

`https://api.meta.org/person?filter=person.name:Dwayne+Casey`

Return a person with publications on a given date:

`https://api.meta.org/person?filter=publicationDate:2019-09-24`

Return a person linked to a given organization:

`https://api.meta.org/person?filter=organization.name:Cornell+University`

### Sorting results
Order results by adding a `sort` parameter to the query string, with the value in the format `field:direction` where direction is either `ASC` or `DESC`.

Results can be sorted by `person.name`.


##### Example
Sort results by descending name:

`https://api.meta.org/person?sort=person.name:DESC`

### Pagination
The API by default returns 500 results per page. You can change this by setting the `limit` parameter, but the maximum
value for that is 500. 

To go to a different page of the results, add a `rowStart` parameter to the query string. The default number of results per page in the API is 500, so to access page 2, 3, 4, etc., you would specify `rowStart=500`,`rowStart=1000`, and so on.

##### Example
To get page four of the results:

`https://api.meta.org/person?rowStart=60`

### Text queries within persons
Text queries are useful for when you are looking for terms within the concepts related to a person.

#### Querying concepts related to a person
Querying by keywords will match keywords of works associated with the person. Add a`keyword` parameter to the query string. 

##### Example
`https://api.meta.org/person?keyword=space+walk`

## Errors
We aim to provide meaningful and clear error responses when they occur. Please let us know where these can be improved.

[insert table of error code, description, etc.]
