<h1 style="margin-bottom:10px;color:#fff;border: none; ">Network Guide - BMW x ScadPro Spring 2024 </h1>

---
<br/>
<br/>

# `/**** Game Server ****/`
# "Game Server Hosting" &nbsp;&nbsp;[📖](https://docs.unity.com/ugs/en-us/manual/game-server-hosting/manual/welcome)
## - Get started &nbsp;&nbsp;[📖](https://docs.unity.com/ugs/en-us/manual/game-server-hosting/manual/guides/get-started#Get_started)

### `'Prerequisites'` &nbsp;&nbsp;[📖](https://docs.unity.com/ugs/en-us/manual/game-server-hosting/manual/guides/get-started#Prerequisites)
### `'Set up Game Server Hosting'` &nbsp;&nbsp;[📖](https://docs.unity.com/ugs/en-us/manual/game-server-hosting/manual/guides/get-started#Set_up_Game_Server_Hosting)
### `'Integrate your game server'` &nbsp;&nbsp;[📖](https://docs.unity.com/ugs/en-us/manual/game-server-hosting/manual/guides/get-started#Integrat)
### `'Create a build'` &nbsp;&nbsp;[📖](https://docs.unity.com/ugs/en-us/manual/game-server-hosting/manual/guides/get-started#Create)
### `'Create a build configuration'` &nbsp;&nbsp;[📖](https://docs.unity.com/ugs/en-us/manual/game-server-hosting/manual/guides/get-started#Create2)
### `'Create a fleet'` &nbsp;&nbsp;[📖](https://docs.unity.com/ugs/en-us/manual/game-server-hosting/manual/guides/get-started#Create3)
### `'Create a test allocation'` &nbsp;&nbsp;[📖](https://docs.unity.com/ugs/en-us/manual/game-server-hosting/manual/guides/get-started#Create4)

## - Tutorials &nbsp;&nbsp;[📖](https://docs.unity.com/ugs/en-us/manual/game-server-hosting/manual/guides/create-a-build)

## - SDK for Unity &nbsp;&nbsp;[📖](https://docs.unity.com/ugs/en-us/manual/game-server-hosting/manual/sdk/game-server-sdk-for-unity)

<br>
<br>

# `/**** Connection ****/`
# "Unity Lobby" &nbsp;&nbsp;[📖](https://docs.unity.com/ugs/en-us/manual/lobby/manual/unity-lobby-service)
The Lobby service allows you to connect players before or during a game session with public or private lobbies. You can use the Lobby service to group players together in a lobby before starting a game session or prevent connection loss if a host player becomes unavailable.

## - Overview &nbsp;&nbsp;[📖](https://docs.unity.com/ugs/en-us/manual/lobby/manual/unity-lobby-service)
> - Browse a list of available game sessions and allow the player to select and join one.
> - Share a join code with your friend to allow them to directly connect to your game session.
> - Use Quick Join to find any available match and jump in.
> - Create a private lobby and send invites to your in-game friends list.
> - Host a lobby from a game server and use it to manage and restrict access to the server session.
> - Query for lobbies that match a specific set of requirements (e.g. game mode, map type).

## - Get started &nbsp;&nbsp;[📖](https://docs.unity.com/ugs/en-us/manual/lobby/manual/get-started#Get_started_with_Lobby)

## - Tutorials &nbsp;&nbsp;[📖](https://docs.unity.com/ugs/en-us/manual/lobby/manual/manage-lobbies)

<br>

# "Unity Matchmaker" &nbsp;&nbsp;[📖](https://docs.unity.com/ugs/en-us/manual/matchmaker/manual/matchmaker-overview)

<br>

# "Relay" &nbsp;&nbsp;[📖](https://docs.unity.com/ugs/zh-cn/manual/relay/manual/introduction#Unity_Relay)
As part of the Unity ecosystem, Relay integrates well with other Unity products, including Lobby, Unity Authentication, Unity Transport Package, Netcode for GameObjects, and the Mirror Networking API.
## - Get started &nbsp;&nbsp;[📖](https://docs.unity.com/ugs/en-us/manual/relay/manual/get-started)

## - Concepts &nbsp;&nbsp;[📖](https://docs.unity.com/ugs/en-us/manual/relay/manual/integration)

## - Use Relay with Netcode for GameObjects (NGO) &nbsp;&nbsp;[📖](https://docs.unity.com/ugs/en-us/manual/relay/manual/relay-and-ngo)

<br>
<br>

# `/**** In Game ****/`
# "Unity NetCode" &nbsp;&nbsp;[📖](https://docs-multiplayer.unity3d.com/netcode/current/about/)

## - Get started &nbsp;&nbsp;[📖](https://docs-multiplayer.unity3d.com/netcode/current/tutorials/get-started-ngo/)

## - How to use Relay server &nbsp;&nbsp;[📖](https://docs-multiplayer.unity3d.com/netcode/current/relay/)
With Netcode for GameObjects you can use an IP address and a port to connect a client to a host over the internet. However, using an IP address to establish a connection doesn't always work. Instead, use Unity Relay to succesfully initiate a connection between multiple clients and a host.

Many factors impact how you connect to the remote host. To connect to a remote host, use one of the following methods:

- Perform a NAT punchthrough: This advanced technique directly connects to the host computer, even if it's on another network.
- Use a Relay server: A Relay server exists on the internet with a public-facing IP that you and the host can access. After the client and the host connect to a relay server, they can send data to each other through the Relay server.

Netcode doesn't offer tools to help you punch through a NAT. However, you can use the Relay service provided by Unity Services to relay all technology based on Unity Transport, like Netcode.

## - Networking components &nbsp;&nbsp;[📖](https://docs-multiplayer.unity3d.com/netcode/current/basics/networkobject/)

### `'NetworkObject'` &nbsp;&nbsp;[📖](https://docs-multiplayer.unity3d.com/netcode/current/basics/networkobject/)
A NetworkObject is a GameObject with a NetworkObject component and at least one NetworkBehaviour component, which enables the GameObject to respond to and interact with netcode.

Netcode for GameObjects' high level components, the RPC system, object spawning, and NetworkVariables all rely on there being at least two Netcode components added to a GameObject:

1. NetworkObject
2. NetworkBehaviour

```c#
// -- Spawning --
// 1) NetworkBehaviour.OnNetworkSpawn() [public virtual void]
// Dynamically Spawned: Awake -> OnNetworkSpawn -> Start
// In-Scene Placed: Awake -> Start -> OnNetworkSpawn
// 2) NetworkBehaviour.OnNetworkDeSpawn() [public virtual void]
```

### `'NetworkObject parenting'` &nbsp;&nbsp;[📖](https://docs-multiplayer.unity3d.com/netcode/current/advanced-topics/networkobject-parenting/)

### `'NetworkBehaviour'` &nbsp;&nbsp;[📖](https://docs-multiplayer.unity3d.com/netcode/current/basics/networkbehavior/)

### `'Physics'` &nbsp;&nbsp;[📖](https://docs-multiplayer.unity3d.com/netcode/current/advanced-topics/physics/)

### `'NetworkManager'` &nbsp;&nbsp;[📖](https://docs-multiplayer.unity3d.com/netcode/current/components/networkmanager/)

### `'NetworkTransform'` &nbsp;&nbsp;[📖](https://docs-multiplayer.unity3d.com/netcode/current/components/networktransform/)

### `'NetworkAnimator'` &nbsp;&nbsp;[📖](https://docs-multiplayer.unity3d.com/netcode/current/components/networkanimator/)

### `'RPC'` &nbsp;&nbsp;[📖](https://docs-multiplayer.unity3d.com/netcode/current/advanced-topics/messaging-system/index.html)
Netcode for GameObjects (Netcode) has two parts to its messaging system: RPCs and Custom Messages. Both types have sub-types that change their behaviour, functionality, and performance.
<br>

![RPC](https://img2023.cnblogs.com/blog/2346211/202302/2346211-20230222180900579-1850279764.png)

### `'NetworkVariable'` &nbsp;&nbsp;[📖](https://docs-multiplayer.unity3d.com/netcode/current/basics/networkvariable/index.html)
At a high level, a NetworkVariable is a way to synchronize a property ("variable") between a server and client(s) without having to use custom messages or RPCs. Since NetworkVariable is a wrapper ("container") of the stored value of type T, you must use the NetworkVariable.Value property to access the actual value being synchronized.
```c#
// NetworkVariable.OnValueChanged()
```

### `'NetworkTime & Ticks'` &nbsp;&nbsp;[📖](https://docs-multiplayer.unity3d.com/netcode/current/advanced-topics/networktime-ticks/index.html)
LocalTime and ServerTime
Why are there two different time values and which one should be used?

Netcode for GameObjects (Netcode) uses a star topology. That means all communications happen between the clients and the server/host and never between clients directly. Messages take time to transmit over the network. That's why RPCs and NetworkVariable won't happen immediately on other machines. NetworkTime allows to use time while considering those transmission delays.
<br>

![NetworkTime](https://img2023.cnblogs.com/blog/2346211/202302/2346211-20230222194311923-543859759.png)
```c#
using Unity.Netcode;
using UnityEngine;

public class MovingPlatform : MonoBehaviour
{
	public void Update()
	{
		// Move up and down by 5 meters and change direction every 3 seconds.
		var positionY = Mathf.PingPong(NetworkManager.Singleton.LocalTime.TimeAsFloat / 3f, 1f) * 5f;
		transform.position = new Vector3(0, positionY, 0);
	}
}

// Ticks
public override void OnNetworkSpawn()
{
	NetworkManager.NetworkTickSystem.Tick += Tick;
}

private void Tick()
{
	Debug.Log($"Tick: {NetworkManager.LocalTime.Tick}");
}

public override void OnNetworkDespawn() // don't forget to unsubscribe
{
	NetworkManager.NetworkTickSystem.Tick -= Tick;
}
```

### `'NetworkRigidbody'`
```c#
/// <summary>
/// Sets the authority differently depending upon
/// whether it is server or owner authoritative
/// </summary>
private void UpdateOwnershipAuthority()
{
	if (m_IsServerAuthoritative)
	{
		m_IsAuthority = NetworkManager.IsServer;
	}
	else
	{
		m_IsAuthority = IsOwner;
	}

	// If you have authority then you are not kinematic
	m_Rigidbody.isKinematic = !m_IsAuthority;

	// Set interpolation of the Rigidbody based on authority
	// With authority: let local transform handle interpolation
	// Without authority: let the NetworkTransform handle interpolation
	m_Rigidbody.interpolation = m_IsAuthority ? m_OriginalInterpolation : RigidbodyInterpolation.None;
}
```

