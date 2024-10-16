# Testing JSON-LD for Access Requests from data.norge.no

## Assumptions

### accessRequesteeType

There exists an extension to dcat-ap-no with URI `http://fellesdatakatalog.digdir.no/vocabularies/dcatnoextension#` which has defined the property `accessRequesteeType`. This property points to a code list which has predefined certain types of actors.

### accessRequesteeTypes

There exists a code list containing i.e. the code `RegisteredOrganization`.

## Try it yourself

The JSON-LD playground at https://json-ld.org/playground/ can be used to test the JSON-LD data and the frames.

The JSON-LD is fetched from data.norge.no:

```bash
curl -H "Accept: application/ld+json" https://data.norge.no/datasets/a49ddd4a-8ccf-3054-8164-0bb9bfc9783c > beregnet_utslipp_entur.jsonld
```

The fetched data can be seen in the file `beregnet_utslipp_entur.jsonld` (NOTE: I have removed several fields which are currently not relevant for this PoC).

If we run JSON-LD framing with the frame defined in `frame.jsonld` the result will be the jsonld file seen in `output.jsonld`.

A shortened version containing the relevant fields can be seen in `abridged_output.jsonld`, which looks like:

```json
{
    "@context": {
      # ...
    },
    "@id": "https://registrering.fellesdatakatalog.digdir.no/catalogs/917422575/datasets/2782049d-1c69-447c-ba64-7daf9a56b5c2",
    "@type": "dcat:Dataset",
    "accessRequesteeType": "RegisteredOrganization",
    "accessRights": "PUBLIC",
    "language": {
      "languageCode": "ENG"
    },
    "publisher": "917422575"
  }
```
