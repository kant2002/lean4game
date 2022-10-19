# Lean 4 Game

This is a prototype for a Lean 4 game platform. It is based on ideas from the [Lean Game Maker](https://github.com/mpedramfar/Lean-game-maker) and the [Natural Number Game
(NNG)](https://www.ma.imperial.ac.uk/~buzzard/xena/natural_number_game/)
of Kevin Buzzard and Mohammad Pedramfar. 
The project is currently mostly copied from Patrick Massot's [NNG4](https://github.com/PatrickMassot/NNG4), but we plan to extend it significantly.

Building this requires a [npm](https://www.npmjs.com/) toolchain. After cloning the repository you should run
`npm install` to pull in all dependencies. For development and experimentation, you can run `npm start` that will perform a non-optimized build and then run a local webserver on port 3000.


## NPM Scripts

* `npm start`: Start the project in development mode. The server will automatically reload when client files get changed. The Lean server will be started without a container. The client and server can be started separately using the scripts `npm run start_client` and `npm run start_server`. The project can be accessed via `http://localhost:3000`.
Internally, websocket requests to `ws://localhost:3000/websockets` will be forwarded to a Lean server running on port `8080`.

* `npm run build`: Build the project in production mode. All assets of the client will be compiled into `client/dist`.
On the server side, the command will set up a docker image containing the Lean server.

* `npm run production`: Start the project in production mode. This requires that the build script has been run. It will start a server on the port specified in the `PORT` environment variable or by default on `8080`. You can run on a specifiv port by running `PORT=80 npm run production`. The server will serve the files in `client/dist` via http and give access to the docker-contained Lean server via the web socket protocol.