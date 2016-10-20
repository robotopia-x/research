# Web RTC Research

MD File to track research progress on Web RTC

## Tasks

* get Audio/Video
* communicate Audio/Video
* communicate data

## Main APIS

### Media Stream

* For Video and Audio  
* getUserMedia(constraints, successCB, erorCB)  
* constraints decide video/audio etc.  
  * video can eg. define resoultion
  * screen capture! 
* optional (can also only use data)

### RTC Peer Connection

* Media Stream into Peer Connection, comes out as Media Stream etc.
* Features:
  * Signal Processing
  * Codex
  * Routing
  * Encrypt
  * Bandwidth
* Offer and Answer
* can transmit to own local peer (useful for testing, can use on same page)

### RTC Data Channel

* requires Peer Connection
* send JSON in Peer
* on data callbacks (similar to socket.io?)
* P2P -> low latency
* reliable/unreliable setting (speed)

#### some API calls
``` javascript
//get connection
pc = new webkitRTCPeerConnection(servers, {optional: [{RtpDataChannels: true}]});
//on data channel initialized
pc.ondatachannel = function(event) {
  receivechannel = event.channel;
  ...
}
// could also use reliable: true
sendchannel = pc.createDataChannel("sendDataChannel", {reliable: false});
```
