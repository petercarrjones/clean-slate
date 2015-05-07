# [expungement-dc](http://codefordc.github.io/expungement-dc/#/)
A simple website for people trying to navigate the process of having records sealed in DC

* As a returning citizen I want to easily and quickly find out if my records are eligible for sealing.
* As a returning citizen, I want step by step information on how to obtain my criminal records in DC.
* As a returning citizen I want to understand my rights in the records sealing process.
* As a returning citizen I want help connecting to legal services for help sealing my record.
* As a returning citizen I want help connecting to other services for returning citizens such as job placement and training.
* As a returning ciizen I want to advocate for progress on issues facing people like me.

* As a legal services provider, I want to have access to forms to assist my client in filing a motion for sealing.

* As an attorney, I want to look up whether an offense is eligible for sealing in DC.
* As an attorney, I want to be able to help a returning citizen breakdown the timeline for sealing eligibility using a chart

---
Additional resources:

- [Flowchart](docs/flowchart.jpeg)
- Requirements ([1](docs/requirements_1.jpeg) & [2](docs/requirements_1.jpeg))

---
####Format Example for [eligibility-flow.json](eligibility-flow.json)

The file starts with two special properties:

1. `"start":"question0"`
start indicates what the initial question should be

2. `"endStates":["eligible", "ineligible", "ineligible at this time"]`
endStates is an array of the possible end states in the flow chart


The remainder of the file is made up of the individual numbered objects contained inside of a parent questions object:
```
questions: {
  "0":{
        "questionText":"Do you have a case pending?",
        "answers":[
           {
              "answerText":"Yes",
              "next":"ineligible at this time"
           },
           {
              "answerText":"No",
              "next":"question1"
           }
        ],
        "helperText":[
           "\"Pending\" refers to any case that is pending or has not been fully resolved. For example, if a case does not have a case disposition, it is likely a case pending."
        ]
     }
}
```


questionText = question that will be displayed for the user 

answerText = words that will be displayed on the buttons

next = which should the user see next if they click this answer? must be the name of a question OR one of the options defined in endStates (see 2. above)

helperText = definitions or explanations of legalese (this can be an empty) `"helperText":[]`

note: If you need to use parentheses, this character must be 'escaped' with a backslash.  For example, "Pending" becomes `\"Pending\"`

---
Developement guide:

    First, make sure that you have [`git`](http://git-scm.com/downloads) on your computer. Create your own [fork](https://guides.github.com/activities/forking/) of the repository, then clone it to your computer:

    git clone git@github.com:[YOUR GITHUB NAME]/expungement-dc.git

	You can work on the `master` branch (which is the default), but it's preferable to set up a new branch if you're working on a specific feature:

    git checkout -b [NEW BRANCH NAME]

---
To Do:

- Add Ineligible Felonies to Step #6 of the wizard
- Add eligible misdemeanor or an ineligible misdemeanor/felony #8
- Adding in additional steps that have not been completed based on the chart.