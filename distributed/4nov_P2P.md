# Peer 2 Peer Systems
<sub>4.nov</sub>

E-mule, Bit-torrent, Napsters are all P2P systems.

P2P systems have no central authority, have a global scale and are made of home computers rather than servers.

<br>
BGP is the routing protocol between autonomus systems. The internet uses autonomous systems, where internally you route however you want.
 The BGP protocol is a fuckin miracle, because every autonomous system announces the IPs it is responsible for. 
 When sensoring the internet Iran tried to change the address of youtube to terminate in Tehran, sensoring on the BGP level. 
 This caused Youtube to be blocked in Iran, but also took down Youtube when for example one tried to reach it from Italy.
  This is because in the BGP system many connections thought that the shortest way to Youtube would be through Iran, which caused the crash. 
  Ergo an absolute miracle that it works.

The tracker is the communication point between the seeders and the leechers.
In the .torrent file, you have information such as the name of the file, sise of each part, hash of parts. 

The seed has all the parts of the file. If you are one of the guys, you ask the tracker for the seed. 
The tracker keeps track of what parts are stored where. After a while the tracker gives a list of 
the guys who have alle the parts, i.e __seeders__, and the ones downloading those parts become the __leechers__ work. 

When spreading the packages throughout the system, you first assign them randomly to get a good spread, and then you use rarest.
Free riders are people who only download, and do not upload. 

Choking algorithms are an important part of BitTorrent. There is a rule about unchoking (unchoking by uploading) where, a peer is given a
 fixed number of peers to upload to. In bitTorrent this is 4. If you connect to a peer, check which part 

 When a peer starts off, the algorithm is extra nice and uses optimistic unchoking, so peers who have nothing to give, upload to other peers,
 still get unchoked and download from other peers.
 
 To solve the problem of the slowest package reamining for a long time, BitTorrent has the __End-game mode__. Take the last package and divide 
 into subparts, where you then download the subparts from different peers. This is BitTorrent-ception. Like the movie Inception, but with BitTorrent, yeah you get it.

 