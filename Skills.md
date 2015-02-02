Semantic Skills Tagging API

Service endpoint URL and parameters

https://api.careerbuilder.com/core/tagging/skills

This URL supports the HTTP/GET and HTTP/POST.

| Parameter | Required | Description |
|-----------|----------|-------------|
| resumecontent | required | A string containing the resume content to be tagged |
| output | optional | A string specifying the desired output format (XML, JSON or Text). Default value is JSON. |
| lan | optional | A string determining the language (total 22 languages supported) in which the input text is written. Default value is en. Note that the input parameter passing to language should be the language id. |
| threshold |optional | An integer (0 - 10) controlling minimum relevancy scores for skill recognition. Higher values will more tightly restrict the returned skill tags. Default is 2. 0 means all seed skill phrases recognized by exact string matching will be returned. Note that this parameter is only supported for inputs in English. |
| auto_thres | optional | A boolean value indicating whether automatic thresholding is desired. If set to true, the threshold parameter will be overwritten to 0 when input text contains no more than 150 words. Default is true.  Note that this parameter is only supported for inputs in English. |


Response

The returned JSON response contains only normalized names in accordance with Wikipedia, If debugging is triggered, corresponding raw terms will be included.
All returned skills are sorted first by relevancy and then alphabetically.
 
