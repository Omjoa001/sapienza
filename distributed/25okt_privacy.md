# PRIVACY
<sub>25.okt</sub>

### TOR - An anonymity system (distributed)
TOR is a service that prevents logging of your browsing. But we also want privacy from the internet provider, the government, and the site you are visiting.

Among the info that makes you indetifiable are your IP address. The libertarians, who seek to maximize autonomy and political freedom, are at play again here when they want privacy. Therefore, TOR, the __Onion Router__. There are a number of __TOR relays__ in the world, say 7000-8000, and you select for instance three of them (three is minimum) randomly. The usual number of relays is five, which by the way are assumed to be byzantine. The first one is called the Guard (dunno why). The last one, the exit point.
Instead of talking to the website directly, you communicate through the guard. The guard with the relay, and the relay with the exit point. Finally, the exit point with the website. The guard knows you but not the website, and the exit point knows the website but not you. 

**K1: Guard, K2:Relay, K3: Exit**

You have a secret key that you have shared with the nodes. It is layered like an onion, first encrypted with K3, then K2, then K1. The guard is able to decrypt the first layer, K3, but has no idea about the IP of the website, which is saved in K3. The guard, after decrypting, sees that the next layer is meant to be decrypted by K2. Guard K1 still has no idea about the final destination. All these layers of encryption hide your communication in the web.

#### How it differs from VPNs

VPNs were not built with privacy in mind. It is solely to make it possible to be part of a local network, even when you are outside. You use a safe protocol to connect to a website, but the VPN provider knows everything about you. 

### Back to the Onion Router

The Guard and the guy in Rome do not have a common key, but using a protocol, in the end those two guys will be the only ones who know about the key. The most famous such key is **Diffie-Helman**. It's the good old use of $ [g^a]^b = [g^b]^a $ to make communication encrypted.

We can use Diffie-Helman to share our key with the guard. Sidenote: We actually use _authenticated Diffie-Helman_, which is an extension to the normal protocol. Here you send the $E_{pk}({g^a})$ to the Guard. The Guard sends the $({g^b}), H({g^{ab}|"handshake")}$. The difference with authenticated is that no one but the guard can decrypt the first message to establish the protocol. You communicate with the other __relays__ through the Guard. You can run a relay at home, even if you are not a libertarian, to participate and help with running TOR and improve society. Sometimes you are the exit point. Sometimes you are the guard. So a guy in LA did the calculations and saw that the most frequent users comes from the following countries: The germans use it most, as well as the chinese, and the italians are in third place. _Crazyyy_. The most used website? Google.

### Performance

When you have multiple relays, you increase latency. In theory you don't lose bandwidth. Realistically, you lose bandwidth because the relays running in a Garage in Tirana or Sydney might have a lousy connection. If the traffic through the Guard, and the Exitpoint is the same, with a say one second delay, you know it is the same person. This is an example of __traffic analysis__ in the system. It is possible to ensure that the guard and the exit node are in different locations. Another possible attack is through the website, by looking at how the browser sends information. The cookies of the exit point can make you unique in a userbase of 200k, breaking your pseudo-anonymity. It still does not know you, but it knows that you are the same guy. To avoid this, you download the __TOR browser__ which has the property that interactions with the website happen the same way. 

<sub></sub>

### The Dark Web
You connect to the __Directory Service__ using TOR. The __hidden service__ waits for connections from the DS. The directory service (DS) knows nothing, because the connections happen using TOR. The DS chooses a rendezvous point, which has no idea where you or the hidden service is and serves as a meeting point for you and the service you want to use. The DS changes every day, and addresses the services with the domain _.onion_. You do not use DNS here.

Alessandro Mei is warning us that when we want to buy drugs or hire killers, we may be scammed. On a lesser note, it is also illegal. Addittionally, remember from the last lection that using bitcoin is not really safe because of the lack of anonymity.


++It is possible to run hidden relays which are not on the public relay list. This is often relevant for example for chinese users.