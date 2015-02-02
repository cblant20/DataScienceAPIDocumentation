Semantic Skills Tagging API

Service endpoint URL and parameters

https://api.careerbuilder.com/core/tagging/skills

This URL supports the HTTP/GET and HTTP/POST methods.

| Parameter | Required | Description |
|-----------|----------|-------------|
| resumecontent | required | A string containing the resume content to be tagged |
| output | optional | A string specifying the desired output format (JSON or XML). Default value is JSON. |
| lan | optional | A string determining the language (total 22 languages supported) in which the input text is written. Default value is en. Note that the input parameter passing to language should be the language id. |
| threshold |optional | A double value between 0 and 1 controlling minimum relevancy scores for skill recognition. Higher values will more tightly restrict the returned skill tags. Default is 0.5. A threshold of 0 means all seed skill phrases recognized by exact string matching will be returned. Note that this parameter is only supported for inputs in English. |
| auto_thres | optional | A boolean value indicating whether automatic thresholding is desired. If set to true, the threshold parameter will be overwritten to 0 when input text contains no more than 150 words. Default is true.  Note that this parameter is only supported for inputs in English. |

Response

The returned response contains only normalized names in accordance with Wikipedia. All returned skills are sorted first by relevancy and then alphabetically.

A sample response with data will look like this:

JSON
{"response":[{"normalized_term":"Apache Hadoop (Hadoop)","confidence":1.0},{"normalized_term":"Apache Hive","confidence":1.0},{"normalized_term":"Softwares","confidence":0.0},{"normalized_term":"Java Platform Enterprise Edition (Computing Platforms)","confidence":0.0}]}

XML
```
<response>
    <skill>
        <normalized_term>SQL Programming</normalized_term>
        <confidence>1.0</confidence>
    </skill>
    <skill>
        <normalized_term>Apache Hadoop (Hadoop)</normalized_term>
        <confidence>0.0</confidence>
    </skill>
    <skill>
        <normalized_term>Ruby on Rails</normalized_term>
        <confidence>0.0</confidence>
    </skill>
</response>
```
And an error response will look like this:

JSON
{"errors":["Unsupported language."]}

XML
```
<errors>
    <error>Unsupported language.</error>
</errors>
```
