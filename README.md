eduCanon's API Documentation
===
Requesting data through the API
---
###Getting an API Key
In order to access eduCanon's API and pull (GET) data, we need to confirm you have the right to access this information. Please email [api@educanon.com](api@educanon.om "api@educanon.com") to request API access.

We need confirmation from all the emails associated with teachers whose data you wish to access through your API key. A sample API key with demo data is __`123456`__

`$api_prefix` = `http://www.educanon.com/apikey/{{API key}}`
	
###GET Teacher Data
Request syntax: `GET $api_prefix/teachers`

- This will return all teachers that can be accessed by your API key.

		//JSON output
		[
        {
          "Teacher" : "Clinton, Bill",
          "TeacherID" : "2"
        }
        ...
        ]
			
###Get Lesson Data
Request syntax: `GET $api_prefix/teachers/{{teacherID}}/lessons`

- This will return all lessons that can be accessed for a given teacher. 
- `{{teacherID}}` is a unique `INTEGER` identifier for a given teacher.

		//JSON output
		[
        {
          "Student" : "Gore, Al",
          "LessonTitle" : "A Tour of the Cell",
          "LessonID" : "22011",
          "TotalLessonPointsEarned" : "2",
          "TimeTaken" : "2014-02-23 20:28:59"
        }
        ...
        ]

Request syntax: `GET $api_prefix/teachers/{{teacherID}}/lessons/{{lessonID}}`

- This will return a single lesson's data with question-by-question breakdown for a given teacher.

- `{{teacherID}}` and `{{lessonID}}` is a unique `INTEGER` identifier for a given teacher and lesson, respectively.


		//JSON output
		[
	    {
	      "Student" : "adams, john",
	      "QuestionText" : "{\"type\":\"multiple_choice\",\"text\":\"<p>What is the first question?<\/			p>\",\"answers\":[\"Answer Choice A\",\"Answer Choice B\",\"Answer choice C\",\"Answer 			Choice D\",\"Answer Choice E\",\"Answer Choice F\",\"Answer Choice G\",\"h\",\"i\",\"j\",			\"k\",\"l\",\"m\",\"n\",\"o\",\"p\"],\"feedbacks\":[\"Explanation A\",\"Explanation B\",			\"Explanatino C\",\"Explanation D\",\"Explanation E\",\"Explanation F\",\"Explanatino G			\"]}",
	      "AnswerSelected":"{\"text\":\"Answer Choice F\",\"index\":5,\"type\":\"multiple_choice\"}",
	      "AnswerCorrect" : "[\"Answer Choice A\"]",
	      "PointsReceived" : "0",
	      "PointsTotalAvailable" : "1",
	      "TimeAnswered" : "2013-08-24 16:48:42"
	    }
	    ...
	    ]
-NOTE: __`QuestionText`__ contains the `type` of question (1 `PointsTotalAvailable` for `multiple_choice` and 3 points `PointsTotalAvailable` for `free_response`), the question `text`, the `answers`, and the `feedbacks` associated with each answer.
