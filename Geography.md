Data Science Team Geography APIs

Contents
- Geocoding API
- Structured queries
- Unstructured queries
- Response
- Nearby Locations API
- Response



Geography Normalization (Geocoding) API
=======================================

Accepts structured or unstructured location information and attempts to resolve the input to a geographic coordinate. If successful, the response will contain one (or more, if requested) locations with latitude and longitude information as well as any available administrative location information, such as country and state. Supports the HTTP/GET method only.

Structured (fielded) queries
----------------------------

Example URL: https://api.careerbuilder.com/core/geography/validate?locality=Atlanta&adminArea=GA&postalCode=30345&country=US

At least one of (locality, postalCode, adminArea, country) must be provided in the query string.


| Parameter  | Description |
|------------|-------------|
| locality   | Optional. The locality, such as the city or neighborhood, that corresponds to an address. |
| adminArea  | Optional. The subdivision name in the country or region for an address. This element is typically treated as the first order administrative subdivision, but in some cases it is the second, third, or fourth order subdivision in a country, dependency, or region. |
| country    | Optional. The name or two-letter ISO code for the country. |
| postalCode | Optional. The post code, postal code, or ZIP Code of an address. |
| culture    | Optional. The preferred ISO 639-1 language code for the response. If this parameter is omitted, the response will be returned in English. Note that the level of localization will vary for each culture. For example, the name "United States" may not have a localized name for every culture code. The geography normalization service currently only supports a subset of the ISO-639-1 standard.|
| maxResults |Optional. Used to specify the maximum number of desired results (up to 20). If this parameter is not specified, the default value of 1 will be used. |


Unstructured (free text) queries
--------------------------------

Example URL: https://api.careerbuilder.com/core/geography/validate?query=Atlanta

| Parameter  | Description |
|------------|-------------|
| query      | Required. A string containing location information. |
| adminArea  | Optional. Used to limit the geographic scope of results to particular administrative area(s). May be added multiple times to limit results to a set of specified administrative areas (of any level), e.g. ?query=London&adminArea=England&adminArea=KY&maxResults=5. |
| country    | Optional. Used to limit the geographic scope of results to a particular country. May be added multiple times to limit results to a set of specified countries, e.g. ?query=Rome&country=IT&country=US&maxResults=10. Note that if both adminArea and country filters are specified (e.g. ?adminArea=GA&country=US), results will be required to match at least one value for each filter. It is therefore not currently possible to request locations in e.g. either Mexico or California. |
|culture     | Optional. The preferred ISO 639-1 language code for the response. If this parameter is omitted, the response will be returned in English. Note that the level of localization will vary for each culture. For example, the name "United States" may not have a localized name for every culture code. The geography normalization service currently only supports a subset of the ISO-639-1 standard. Click to toggle a full list of supported culture codes. |
| maxResults | Optional. Used to specify the maximum number of desired results (up to 20). If this parameter is not specified, the default value of 1 will be used. |

Geocoding API Response
----------------------

The returned JSON response will be formatted identically for both request types.

| Field    | Description |
|----------|-------------|
| errorMsg | Contains information about any error(s) incurred during the request. If the request successfully returns results, this field will be empty. |
| geoData  | A JSON array of one or more objects containing geography data. If the request returns no results, the array will be empty. |

For successful requests, each element of the returned array will be formatted as follows:

|   |   |
|---|---|
| AdminAreas A JSON array of up to 2 AdminArea objects. Name: The name of the administrative district or subdivision. Level: An integer (1 or 2) indicating the hierarchal level of the administrative area. |
| Latitude | A double value specifying the location's latitude (in degrees) within the range [-90, +90]. |
| Longitude | A double value specifying the location's longitude (in degrees) within the range [-180, +180]. |
| Country | The country or region name of an address. |
| City | The populated place for the address. This typically refers to a city, but may refer to a suburb or a neighborhood in certain countries. |
| PostalCode | The post code, postal code, or ZIP code of an address. |
| CountryCode | The two-letter ISO country code. |
| LocationType | The classification of the geographic entity returned, such as City or Coordinate. |
| StreetAddress | The official street line of an address relative to the area, as specified by the Locality, or PostalCode, properties. |
| Landmark | The full name of the landmark (such as a military base or island) returned by the service. If the returned entity is not a landmark, this field will be empty. |


Nearby Locations API
--------------------

Accepts latitude and longitude values representing a geographic point and attempts to return a list of populated places near the point, sorted in descending order of population.

Example URL: https://api.careerbuilder.com/core/geography/nearbylocations?lat=33.75&lon=-84.39

| Parameter | Description |
|-----------|-------------|
| latitude | Required. The latitude part of the coordinate query. May be shortened to lat. |
| longitude | Required. The longitude part of the coordinate query. May be shortened to lon. |
| language | Optional. The preferred ISO 639-1 language code for the response. May be shortened to lang. If this parameter is not specified, the default value of en (English) will be used. |
| radius | Optional. An integer value (in km) indicating the maximum distance of a returned location from the provided point (up to 300 km). May be shortened to rad. If this parameter is not specified, the default value of 30 km will be used. |
| maxResults | Optional. Used to specify the maximum number of desired results (up to 100). If this parameter is not specified, the default value of 10 will be used. |
| sortBy | Optional. Used to specify the value by which to sort results. Accepted values are "population" (default) and "distance". Note that in cases where not all results are returned, the set of results returned for one sorting parameter will often contain different results than those returned for the other sorting parameter. |

Nearby Locations API Response
-----------------------------
|   |   |
|---|---|
| errorMsg | Contains information about any error(s) incurred during the request. If the request successfully returns results, this field will be empty. |
| geoData | A JSON array of one or more objects containing geography data. If the request returns no results, the array will be empty. |  

For successful requests, each element of the returned array will be formatted as follows:

|   |   |
|---|---|
| AdminAreas | A JSON array of up to 2 AdminArea objects, each formatted as follows: Name: The name of the administrative district or subdivision. Level:  An integer (1 or 2) indicating the hierarchal level of the administrative area. |
| AdminArea | The top-level administrative division of the named populated place (typically a state or province). |
| CountryCode | The two-letter ISO-3166 country code representing the country of the named populated place. |
| CountryName | The country of the named populated place. |
| Distance | The distance, in km, of the named populated place from the geographic coordinate supplied in the request. |
| Latitude | The latitude part of the named populated place's geographic location. |
| Longitude | The longitude part of the named populated place's geographic location. |
| Name | The name of the populated place. |
| Population |The population of the named populated place. |
