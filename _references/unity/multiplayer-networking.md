---
# BASICS
refid    : rMultiplayerNetworking
title    : "Multiplayer Networking"
date     : 2015-11-02
subtitle : "How to setup Multiplayer Networking in Unity."
author   : aStardog

# IMAGES
bg-img-path  : "001.jpg"
bg-img-scale : 250%

# OPTIONS - REFERENCE
isAvailable    : false
type           : unity
rel-tutorials  : [tRocketTournament]
rel-references : [rClass]

# OPTIONS - GENERAL
isPublic : true
---
**UNet** is the name of Unity's Networking system. Please see the <a href="http://docs.unity3d.com/Manual/UNetOverview.html" class="external">official docs</a> for more info.

* TOC
{:toc}

## Basics
These are some basic concepts that you must understand before you can make your game multiplayer.

* Everthing should go through the Server.
  * Server
  * Clients read the position/rotation of dynamic objects from the Server.
  * Clients send their data (could be position/rotation info, etc) to the Server, so it can be read by other Clients.
* GameObjects that need to be networked must have a <a class="external" href="http://docs.unity3d.com/ScriptReference/Networking.NetworkIdentity.html">NetworkIdentity</a> component.
* Scripts with values that need to be networked must inherit from <a class="external" href="http://docs.unity3d.com/ScriptReference/Networking.NetworkBehaviour.html">NetworkBehaviour</a>.

When you are connected to a Server as a Client. All the other players you see running around are empty shells. They have enough scripts attached to position/rotate them, drive animations, and that's it.

### Server, Host, Client
* Server is dedicated machine
* Host is a Server and a Client
* Client is someone who connects to the Server

## Commands
Commands are the way for clients to request to do something on the server.

* http://docs.unity3d.com/Manual/UNetActions.html
* http://docs.unity3d.com/Manual/class-NetworkBehaviour.html

* Function only runs on server's machine.
* Called from client to server, or server to server. 
* Can only be run from your own player object (isLocalPlayer must be true?), unlike RPC's.
* Must be prefixed Cmd, e.g. CmdFunctionName().
* Parameters must be simple (int, float, Vector3, bool, struct, GameObject[1][2], NetworkIdentity[1][2], etc).
  * http://answers.unity3d.com/questions/1001474/unet-parameter-restrictions-for-command-and-client.html
  * [1] http://forum.unity3d.com/threads/networkserver-findlocalobject-networkinstanceid-netid.327114/#post-2121215
  * [2] http://forum.unity3d.com/threads/how-do-i-synchronize-gameobjects-or-components.347241/#post-2247157
* Instantiating objects (that show for everyone) must be done by server using NetworkServer.Spawn. If client is trying to do it, it must use a Command. Instantiate as normal on the server, then call "NetworkServer.Spawn(objInstance)" to make it appear to all clients.
* (?) To send reference to GameObject as parameter, send its netId (NetworkInstanceID). Can be found from its NetworkIdentity component.
  * http://forum.unity3d.com/threads/networkserver-findlocalobject-networkinstanceid-netid.327114/#post-2121215
    * "Just pass the GameObject (or NetworkIdentity) as a parameter to the ClientRpc call and the system will look it up for you."
* Client cannot access an "unowned" network object to run functions on it via GetComponent. To run a function on another object, it must be done by the server. The client, at the point of wanting to access the unowned object, should instead run a Command to make the server access it.
  * Example: Client has detected a button via raycast. It wants to use "buttonGO.GetComponent<Button>().Press()" on the button, but can't, even if it's a Command. Instead, replace it with "CmdPressButton(buttonGO.GetComponent<NetworkIdentity>().netId)"
  * The code inside the CmdPressButton(NetworkInstanceId id) will contain "GameObject targetGO = NetworkServer.FindLocalObject(id);", and "targetGO.GetComponent<Button>().Press()".
  * The server has now called the Press() function on its machine. If the client is hooked to any SyncVars/SyncEvents that change, it can run a hook function, but if not, the Press() ran by the server should call an RpcPress() function.
* Cannot return values (?)

## RPC's
...

## Execution order
Here is the order that various functions are called. Note, there are some functions that could be called at any time.

### NetworkManager (as host)
Execution order when hosting your own game, and playing as a Client.

* StartHost()
* OnStartHost()
* OnStartServer()
* OnServerConnect(NetworkConnection conn)
* OnStartClient(NetworkClient client)
* OnServerReady(NetworkConnection conn)
* OnServerAddPlayer(NetworkConnection conn, short playerControllerId)
* OnClientConnect(NetworkConnection conn)

### Anytime
* OnServerDisconnect(NetworkConnection conn)
* OnClientDisconnect(NetworkConnection conn)

## Example Situations
Here are some situations that you might wish to create in a multiplayer setting.

### Button that opens a local door
There is a button that opens a door. Any player can use this button.

The Button script has a Press() function, which will send an Event (ButtonPressed).

The Door script will listen for this Event, then run either its Open() or Close() function.

The problem is that, as a connected client, you cannot use the button. It's a NetworkBehaviour that you cannot affect.

The Server is the one that must use the button.

## Notes
* <a class="external" href="http://docs.unity3d.com/Manual/UNetOverview.html">Networking Overview</a>
* <a class="external" href="http://docs.unity3d.com/Manual/UNetReference.html">Networking Reference</a>
* http://forum.unity3d.com/threads/new-multiplayer-tutorial.385849/
* Unite 2016 - Building Multiplayer Games with Unity - https://www.youtube.com/watch?v=-_0TtPY5LCc

