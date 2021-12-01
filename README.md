# 42_ft_transcendence (@42Paris)

> This project is running with Docker. You need to install it before. Here is the [subject][1].
>

*"Soon you will know that you’ve already known things that you thought you didn’t know"*

<p align="center">
  <img src="https://i.pinimg.com/originals/d7/65/ca/d765cadd577d6901922c2bfcd8419015.gif">
</p>

## About

Ft_transcendence is the last project of the mandatory part of the cursus that I made with [Helene Herin][2], Yassine El Alouani and Quentin Roland.
<br/><br/>The goal of this project was to create from scratch a web application, and more precisely a multiplayer pong game respecting some requirements:
- :white_check_mark: : Frontend and backend should be wrote only in Typescript.
- :white_check_mark: : NestJS framework was mandatory for backend.
- :white_check_mark: : We had to use PostgreSQL as database.
- :white_check_mark: : We were free to select a Typescript framework for frontend, and we choose Vue.js.
- :white_check_mark: : The web application should be built using Docker-Compose.
- :white_check_mark: : Each service (front, back and DB) should be running in its own container.
- :white_check_mark: : Data must be persistent (using Docker volumes).

## Pong web application in depth

The project could be splitted in 4 differents parts : authentification and security concerns, user account, chat and pong game.

#### :key: : SECURITY (Quentin Roland)
Authentification to the web application is made with the use off a JWT token, working either with 42 API login or with a classic username / password. You can also activate 2FA authentification. All routes are protected in the backend using NestJS guards. Input fields are also protected against wrong inputs.

#### :bust_in_silhouette: : USER ACCOUNT (Quentin Roland)
You will be able to modify your username and your avatar. You will also see your match history, with number of victories / losses and your score. You can manage your own friend list, add other users, see their profile / status, and block someone if needed.

#### :iphone: : CHAT (Yassine El Alouani)
You can create public channel (with password or not), giving you admin rights on this channel. As an admin, you can mute or ban other users, or give them moderator rights if you need some help to manage the cannel. You can also send private messages to other users, off course if they didn't block you previously. 
<br/><br/>The whole chat is built using websocket, so that each action you made is totally instant, like kicking someone off a channel, sending a message to another user, or muting a disturbing user.

#### :video_game: : PONG GAME (Helene Herin && Lucas Lefrancq)
You will first before matchmaking be asked to choose your favorite game options. Matchmaking will start after clicking on the `START GAME` button. You will be matched only with player who have chosen same difficulty level and same score limit. Paddle color doesn't matter, it's just a customization option.
<br/><br/>When finally matched with another player, the game can start. 
<br/>Use your mouse (or your finger if you're on mobile phone) to control the paddle and score some points. The first one to reach the score limit win the game !
<br/><br/>Game algorithm is implemented inside the backend, so nobody can interfer with it and try to cheat. Frontend / backend communicate with websockets, so every movement made by a player is instantly perceived by the other player. Pong animation is made with Canvas. Disconnections are also handled.

## Building and running the project

1. Download/Clone this repo

        git clone https://github.com/llefranc/42_ft_transcendence

2. `cd` into the root directory and run `make install`. This will create the containers, install the node modules, and run the containers.

        cd 42_ft_transcendence
        make install

3.  Go to http://localhost:8080 using your favorite browser. Enjoy ! 

        Note : to try all the features, open a private window and login with another account.
		You will be then able to launch a pong game, chat with the other user...

4. At the end, run `make remove` to stop the containers, destroy them and remove the volumes.
	
		make remove

[1]: https://github.com/llefranc/42_ft_transcendence/blob/main/ft_transcendence.en.subject.pdf
[2]: https://github.com/hherin