# official-KaldiWebrtc

This is a demonstration of realtime online speech recognition using the Kaldi speech recognition toolkit.

It uses WebRTC to communicate between the server and the browser. It sends audio from the user's microphone using the WebRTC audio track and sends text from the server to the browser using the WebRTC datachannel (most commonly used for sending chat messages).

The server program is written in Python. It uses aiohttp to display the web-page and serve other static data (javascript, CSS. images). For WebRTC functionality it uses the excellent aiortc library. The system requires only one Python server running, but supports multiple Kaldi instances in the background. Once it receives a request from the browser it opens a connection to the Kaldi engine and keeps forwarding audio and text between Kaldi and the user's browser.

# Usage

You just need to have Docker installed and run the commands as described below.

In addition to Docker, you will need to have the docker-compose program installed. 
This program allows to easily start several containers at once simply by changing the configuration in a yml file.

To run the server, simply copy the [docker-compose.yml](docker-compose.yml) and the required 
[servers.json](servers.json) files into a folder of your choice and run: `docker-compose up -d`

First time you run it, the program will download the images from Dockerhub so it may take a little while. Once it's running,
you can run `docker-compose logs -f` to monitor the logs of the running servers.

At any time you can run `docker-compose stop` to temporarily shutdown and `docker-compose start` to restart the service.
Finally, you can run `docker-compose down` to stop and remove the containers altogether.
