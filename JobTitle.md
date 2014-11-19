
b title classification service is available for use outside the firewall. You will need to reach out to APIandAuthDevelopment for credentials in order to use it, and further instructions for setup can be found in this document.
 
I don’t have a link to online documentation yet, but will pass that along when it becomes available. For the time being, brief documentation is below:
 
Production link: https://api.careerbuilder.com/core/classifier/jobtitle
Test link: https://wwwtest.api.careerbuilder.com/core/classifier/jobtitle
 
HTTP method: GET or POST
Parameters (query/form):
-        taxonomy (required) : classification taxonomy to use; allowable values are onet15, onet17, carotenev1, carotenev2
-        title (required) : job title
-        description : job title description
-        outputType : response format, defaults to json; allowable values are json, xml
 
Example: https://api.careerbuilder.com/core/classifier/jobtitle?taxonomy=onet15&title=janitor&outputType=xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<titleList>
    <titles>
        <title>Janitors and Cleaners, Except Maids and Housekeeping Cleaners</title>
        <id>37-2011.00</id>
        <confidence>90.0</confidence>
    </titles>
    <titles>
        <title>First-Line Supervisors/Managers of Housekeeping and Janitorial Workers</title>
        <id>37-1011.00</id>
        <confidence>56.0</confidence>
    </titles>
</titleList>
