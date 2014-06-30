#### PEOPLE.CO BATTLESHIP CHALLENGE

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

URL https://student.people.co/api/challenge/battleship/<user_id>/boards  
GET returns a JSON list of board objects  
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
