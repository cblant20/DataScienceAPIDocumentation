After months of getting its development pushed back, I am pleased to inform you that the job level classifier service is now, finally, available for use in test and production.
 
This service will attempt to determine the level (i.e. seniority, expected experience) of a job based on its title. It will return a value from 1 to 5, along with a brief description.
 
The service is located at https://api.careerbuilder.com/core/tagging/joblevel. As usual, you will need OAuth credentials to use this service.
 
Here is an example input:
api.careerbuilder.com/core/tagging/joblevel?title=software engineer
 
And the corresponding output:

{"text":"software engineer", "level":"3", "description":"Experienced (non-Manager)"}
 
Input should be provided using the title= query parameter. The output will always contain the following three fields for a valid input:
 
text: the provided title

level: an integer between 1 and 5 indicating the job’s level

description: a brief description corresponding to the level
 
Following are all of the possible level + description pairs:
1 Internship

2 Entry Level

3 Experienced (non-Manager)

4 Manager (Manager, Supervisor of Staff)

5 Executive (VP, SVP, Department Head, President, etc)
 
Please let me know if you have any questions or concerns.
