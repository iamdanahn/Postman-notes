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

### Pre-request Scripts
Based on the response, it will add the list of players and set it to the
`player_id` key in the set Environment
This `player_id` can be used anywhere as long as the Environment is set

If not environment is set, variables can still be used if set up in the `TEST` with scripts
```js 
if(!pm.variables.get('player_id')) pm.variables.set('player_id', -1);
```
