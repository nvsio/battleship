#### People.Co Battleship Challenge

Battleship is a classic two­-player guessing game which many of you may have played in actual board game or electronic form. In this challenge, you will make a virtual battleship player.

Important Links:  
[Challenge Interface](https://student.people.co/#/home/battleship2014)  
[Code Submission Form](https://docs.google.com/a/nvs.io/forms/d/11k06x4EE6ZPURWoiblV-ybr_KF2M8JOMK7OZMTYcSmU/viewform)  
[Tech Draft 2014 Support Chatroom](https://www.hipchat.com/g9Yih0LlG)  

##### Objective

Develop a program that acts like an intelligent battleship player and minimizes the number of “shots” required to find and sink all of the opposing player’s ships.

If you have not played battleship, here’s how our variant of it works. Each game board is a 10x10 grid, with columns labeled A-J and rows labeled 1-10. A location on the board consists of the row number appended to the column letter, eg: A1, C7, J10. The server will randomly lay out five ships on non-overlapping parts of the board. The names of ships and the number of squares each ship occupies is:
- carrier (5 squares)
- battleship (4 squares)
- submarine (3 squares)
- destroyer (3 squares)
- patrol (2 squares)

You submit a “shot” to a location on the board, and the server will tell you if that shot is a “hit” or a “miss”. To sink a ship, you must submit shots to all of the squares that ship occupies. In the event one of your shots does sink a ship, the server will also tell you which ship you sank. A game board is finished when you have sunk all five ships.

##### Battleship Player API

Your program is expected to play Battleship using a simple HTTP API. You API urls may be found on the [Challenge Interface](https://student.people.co/#/home/battleship2014). NOTE: These URLs are unique to each player - please do not share them with each other. Below is documentation for the accepted HTTP methods and response formats for each URL:

```
URL https://student.people.co/api/challenge/battleship/<user_id>/boards  
GET returns a JSON list of board objects  
```

Example success response (HTTP 200):

```
[
 {
  "board_id": "live_board_1",
  "url": "https://student.people.co/api/challenge/battleship/2deb6109356e/boards/live_board_1", "is_test": false,
  "is_finished": false
 },
 {
  "board_id": "test_board_1",
  "url": "https://student.people.co/api/challenge/battleship/2deb6109356e/boards/test_board_1", "is_test": true,
  "is_finished": false
 }
]
```

Note that each board object includes a URL to that specific board as well as the board’s id and info about whether or not it is finished and whether or not it is a test board.

```
URL https://student.people.co/api/challenge/battleship/<user_id>/boards/<board_id>  
GET returns a single JSON board object  
```

Example success response (HTTP 200):

```
{
 "board_id": "test_board_1",  
 "is_test": true,  
 "is_finished": false,  
 "shots": 0,  
 "sunk_carrier": false,  
 "sunk_battleship": false,  
 "sunk_submarine": false,  
 "sunk_destroyer": false,  
 "sunk_patrol": false  
}
```

Note that this board object contains the current state of the board, including information about how many shots the player has fired on the board and which ships they have sunk.

DELETE resets the board object and deletes all “shots”.  
If the board was test board and the reset was successful, the response will be an HTTP 200.  
If the board was a live board and the reset was not successful, the response will be an HTTP 400.  

```
URL https://student.people.co/api/challenge/battleship/<user_id>/games/<board_id>/<shot_location>  
POST submits a shot to that location and returns whether or not there was a hit  
```

Example success response (HTTP 200):

```
{
 "board_id": "test_board_1",  
 "location": "A1",  
 "is_hit": false,  
 "is_finished": false,  
 "sunk": null  
}
```

In addition to information about whether or not the shot was a hit, the shot response also tells you if this specific shot sunk a shop and if that specific shot won the game. If this specific shot sunk a ship, then “sunk” will have one of the following values: “carrier”, “battleship”, “submarine”, “destroyer”, “patrol” depending on which boat was sunk. If the specific shot sunk the last ship and the board is finished, “is_finished” will also be returned as true and there is no need to make any more shots to the same board.

Note that GET on this URL will also fire a shot and return an identical response. While this is strictly a violation
of HTTP API conventions, it simplifies testing and integration with many programming languages which is why we made it an option.

##### Rules and Submission

Your battleship player code may be written in any language and use any tools, libraries, or utilities you like. The winning programs are the ones which use the fewest number of “shots” to win all of the non­test boards. Shots fired against the boards affect the challenge interface leaderboard, but do NOT affect the final ranking.  

Before the end of the challenge period, you must do the following:
- Use your program to finish all available boards
- Submit your battleship player code

A submission consists of:
- Your name and email address (associated with your Tech Draft Application)
- Link to a single public git repo hosted by either GitHub or BitBucket that contains your submission.
- README.md or README.txt file in its root which contains a description of the utility and examples of how to run it.

To submit your entry, fill out the [submission form](https://docs.google.com/a/people.co/forms/d/11k06x4EE6ZPURWoiblV-ybr_KF2M8JOMK7OZMTYcSmU/viewform).
- Once you submit, hang onto the edit URL in case you need to modify your submission.
- You may submit this form at any time and modify it throughout the entire duration of the
challenge ­ we will only review the submissions at the end of the challenge.







