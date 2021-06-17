## Basic notes
Collections can be edited to hold "Authorizations"
Inside, Key Value pairs can be sent as Authorization headers whenever sending
an API request.

Variables can be saved for portions of the URI.
This saves time and minimizes chances for typos
To see variable values, hover over the var


## Test Scripts
Tests can be made per request in the "Test" tab 
```js
pm.test('Status code is 200', function () {
    pm.response.to.have.status(200); 
});
```
^ this checks to see if the Response Code === 200
`pm.test` uses the first text string parameter to ouput he test result in Postman
Test results show on the bottom section next to Headers

If it passes, `PASS` and only the first argument will show
`PASS Status code is 200`
If no pass, `FAIL`, first arg, and error will show
`FAIL Status code is 200 | AssertionError: expected response to have status code 400 but got 200`

Environments can be setup in the top right corner next to the eye

Scripts can be added to the "TEST" tabs like below:
```js
var player_list=pm.response.json().data.players;
pm.environment.set('player_id', player_list[Math.floor(Math.random() * player_list.length)].id);
```

## Pre-request Scripts
Based on the response, it will add the list of players and set it to the
`player_id` key in the set Environment
This `player_id` can be used anywhere as long as the Environment is set

If not environment is set, variables can still be used if set up in the `TEST` with scripts
```js 
if(!pm.variables.get('player_id')) pm.variables.set('player_id', -1);
```

Several requests can be run at once via the `Runner` tab on the top left window
Pick the: 
- Requests you want to run
- Environment to enable certain variables (Enable 'Keep variable values')
- Any other settings as required

NOTES:
`pm` - seems to stand for Postman
It has methods attached to it that can be used when scripting

```js
console.log(pm.response.json().rand)
pm.environment.set("responseData", pm.response.json().rand);
```

pm.response.json().rand
^ grabs the response object and returns the JSON version of it
then keys into the `rand` key

```json
{
    "welcome": "You're using the Postman Skill Checker! Click Visualize for a more readable view of the response.",
    "title": "Skill checker complete!!!",
    "intro": "You completed the skill checker! To complete your training, make sure all of your requests are saved, and in the collection on the left of Postman, open the overview > then click **Share**. Choose **Get public link** and generate or update your collection link (note that each time you make a change you need to update the link). Copy the address to your clipboard, then open the final folder in the collection **3. Check Progress** > open the **Test Collection** request, paste your collection link in as the request address, **Send**, and this time open the **Test Results** tab to see the status of your collection. Any failed tests will indicate parts of the collection you still need to complete. Once all of your tests pass—**Save** the request and send the collection link via this form (the Postman team will check your submission and award your student expert certification within a couple of weeks! 📜🎓): bit.ly/student-expert-submission",
    "done": true,
    "skills": [
        {
            "name": "Changed method",
            "hint": "Change the request method to `POST`, `PUT`, or `DELETE`.",
            "value": true
        },
        {
            "name": "Sent query parameter",
            "hint": "Add `email` as a query param, with your student training email address as the value.",
            "value": true
        },
        {
            "name": "Added body data",
            "hint": "Add JSON body data including a field `name` with the value as your name.",
            "value": true
        },
        {
            "name": "Authorized",
            "hint": "Add API Key auth with the Key name `auth_key` and how much you learned from the student expert template (e.g. `loads`, `nothing`, etc) as the value (add to the request header).",
            "value": true
        },
        {
            "name": "Set a variable",
            "hint": "Add a new variable to the collection, naming it `myCourse` and enter the reason you're learning about APIs as the Current value. (Leave the other var in place.)",
            "value": true
        },
        {
            "name": "Added a script",
            "hint": "Add a test script that gets the value of the `rand` property in the response JSON and sets it as the value of a variable (at collection or environment scope) named `responseData`. Hint: You'll need to Send the request twice after adding your code because it won't save the value until after the response is received the first time.",
            "value": true
        }
    ],
    "rand": "Dayton"
}
```