Hello friends,
 
The Relevant Skills API is now available at https://api.careerbuilder.com/core/tagging/relevantskills. Impress your friends and family by suggesting valuable skills relevant to the ones they already have! As usual, you will need to complete the OAuth handshake and provide a valid token in order to access this service.
 
Here are some facts about this service:
 
·       Accepts one or more skill names (pipe-separated) and outputs a list of relevant skills for each, sorted by relevance
·       Returns a response in JSON or XML format (using the output query parameter; default is JSON)
·       Totally cool
 
An example call looks like this:
https://api.careerbuilder.com/core/tagging/relevantskills?skillname=writing&output=xml

    <response>
        <skillsData>
            <skillName>writing</skillName>
            <relevantSkill>
                <normalizedName>Stand-Up Comedy</normalizedName>
                <score>0.591823</score>
            </relevantSkill>
            <relevantSkill>
                <normalizedName>Hapkido</normalizedName>
                <score>0.588954</score>
            </relevantSkill>
            <relevantSkill>
                <normalizedName>Creative Writing (Writing)</normalizedName>
                <score>0.588566</score>
            </relevantSkill>
            (…lots more skills…)
        </skillsData>
    </response>
 
Here is another example, this time passing multiple skills and receiving a JSON response (the default format):
https://api.careerbuilder.com/core/tagging/relevantskills?skillname=java|hadoop

    {
      "skillsData": [
        {
          "skillName": "c",
          "relevantSkills": [
            {
              "normalizedName": "C++ (Programming Language)",
              "score": 0.784706
            },
            {
              "normalizedName": "Java",
              "score": 0.727388
            },
            (…lots more C-related skills…)
          ]
        },
        {
          "skillName": "hadoop",
         "relevantSkills": [
            {
              "normalizedName": "Apache HBase (BigTable Implementations)",
              "score": 0.851156
            },
            {
              "normalizedName": "Apache Hive",
              "score": 0.849868
                 },
            (…lots more Hadoop-related skills…)
        ]
        }
    ]
    }
 
Please let me know if you have any questions or feedback.
 
Thanks!
 
Thomas
