---
sidebar_position: 4
title: CharacterClass
hide_title: true
sidebar-label: 'CharacterClass'
---

<br></br>

### CharacterClass
A script class that is instanced for every [Character](/lua/Game-Script-Environment/Userdata/Character) in the game.

A [Character](/lua/Game-Script-Environment/Userdata/Character) is a temporary vessel controlled by a [Player](/lua/Game-Script-Environment/Userdata/Player) or [Unit](/lua/Game-Script-Environment/Userdata/Unit).

The class can receive events sent with [sm.event.sendToCharacter](/lua/Game-Script-Environment/Static-Functions/sm.event#sendtocharacter).

The fields below are accessed using <code>self.fieldName</code> in the CharacterClass script:

<strong>Fields:</strong>

| Type        | Name           | Description |
| ----------- | -----------    | ----------- |
| [Character](/lua/Game-Script-Environment/Userdata/Character) | character | The [Character](/lua/Game-Script-Environment/Userdata/Character) game object belonging to this class instance. |
| [Network](/lua/Game-Script-Environment/Userdata/Network) | network | A [Network](/lua/Game-Script-Environment/Userdata/Network) object that can be used to send data between client and server. |
| any | data | Data from the <code>data</code> entry in the character's JSON file entry. |

<strong>Callbacks:</strong> <br></br>

## Client-only

### onProjectile

```lua
function CharacterClass.client_onProjectile(self, position, airTime, velocity, projectileName, shooter, damage, customData, normal, uuid)
end
```
Called when the [Character](/lua/Game-Script-Environment/Userdata/Character) is hit by a projectile.

:::info note
If the shooter is destroyed before the projectile hits, the shooter value will be nil.
:::

<strong>Arguments:</strong> <br></br>

- <code>self</code> [<strong> table </strong>]: The class instance.
- <code>position</code> [<strong> vec3 </strong>]: The position in world space where the projectile hit the Character.
- <code>airTime</code> [<strong> number </strong>]: The time, in seconds, that the projectile spent flying before the hit.
- <code>velocity</code> [<strong> vec3 </strong>]: The velocity of the projectile at impact.
- <code>projectileName</code> [<strong> string </strong>]: The name of the projectile. (Legacy, use uuid instead)
- <code>shooter</code> [<strong> player/unit/shape/harvestable/nil </strong>]: The shooter. Can be a Player, Unit, Shape, Harvestable or nil if unknown.
- <code>damage</code> [<strong> int </strong>]: The damage value of the projectile.
- <code>customData</code> [<strong> any </strong>]: A Lua object that can be defined at shoot time using <code>sm.projectile.customProjectileAttack</code> or any other custom version.
- <code>normal</code> [<strong> vec3 </strong>]: The normal at the point of impact.
- <code>uuid</code> [<strong> uuid </strong>]: The uuid of the projectile.

---

### onMelee

```lua
function CharacterClass.client_onMelee( self, position, attacker, damage, power, direction, normal )
end
```
Called when the [Character](/lua/Game-Script-Environment/Userdata/Character) is hit by a melee attack.

:::info note
If the attacker is destroyed before the hit lands, the attacker value will be nil.
:::

<strong>Arguments:</strong> <br></br>

- <code>self</code> [<strong> table </strong>]: The class instance.
- <code>position</code> [<strong> vec3 </strong>]: The position in world space where the Character was hit.
- <code>attacker</code> [<strong> player/nil </strong>]: The attacker. Can be a Player or nil if unknown. Attacks made by a Unit will be nil on the client.
- <code>damage</code> [<strong> int </strong>]: The damage value of the melee hit.
- <code>power</code> [<strong> number </strong>]: The physical impact of the hit.
- <code>direction</code> [<strong> vec3 </strong>]: The direction of the melee attack.
- <code>normal</code> [<strong> vec3 </strong>]: The normal at the point of impact.

---

### onCollision

```lua
function CharacterClass.client_onCollision( self, other, position, selfPointVelocity, otherPointVelocity, normal )
end
```
Called when the [Character](/lua/Game-Script-Environment/Userdata/Character) collides with another object.

<strong>Arguments:</strong> <br></br>

- <code>self</code> [<strong> table </strong>]: The class instance.
- <code>other</code> [<strong> shape/character/harvestable/lift/nil </strong>]: The other object. Nil if terrain.
- <code>position</code> [<strong> player/nil </strong>]: The position in world space where the collision occurred.
- <code>selfPointVelocity</code> [<strong> int </strong>]: The velocity that that the Character had at the point of collision.
- <code>otherPointVelocity</code> [<strong> number </strong>]: The velocity that that the other object had at the point of collision.
- <code>normal</code> [<strong> vec3 </strong>]: The collision normal between the Character and the other object.

---

### onGraphicsLoaded

```lua
function CharacterClass.client_onGraphicsLoaded( self )
end
```
Called when graphics are loaded for the [Character](/lua/Game-Script-Environment/Userdata/Character).

After this, graphics related functions can be called, like accessing animations.

<strong>Arguments:</strong> <br></br>

- <code>self</code> [<strong> table </strong>]: The class instance.

---

### onGraphicsUnloaded

```lua
function CharacterClass.client_onGraphicsUnloaded( self )
end
```
Called when graphics are unloaded for the [Character](/lua/Game-Script-Environment/Userdata/Character).

After this, graphics related functions no longer have any effect or will fail.

<strong>Arguments:</strong> <br></br>

- <code>self</code> [<strong> table </strong>]: The class instance.

---

### onInteract

```lua
function CharacterClass.client_onInteract( self, character, state )
end
```
Called when a [Player](/lua/Game-Script-Environment/Userdata/Player) is interacting with the [Character](/lua/Game-Script-Environment/Userdata/Character) by pressing the <code>Use</code> key (default <code>E</code>).

<strong>Arguments:</strong> <br></br>

- <code>self</code> [<strong> table </strong>]: The class instance.
- <code>character</code> [<strong> character </strong>]: The Character of the Player that is interacting with this Character.
- <code>state</code> [<strong> bool </strong>]: The interaction state. Always true. The <code>CharacterClass</code> only receives the key down event.

---

### canInteract

```lua
function CharacterClass.client_canInteract( self, character )
	return true --true or false, default true if onInteract is implemented
end
```
Called to check whether the [Character](/lua/Game-Script-Environment/Userdata/Character) can be interacted with at this moment.

:::info note
This callback can also be used to change the interaction text shown to the player using [sm.gui.setInteractionText](/lua/Game-Script-Environment/Static-Functions/sm.gui#setinteractiontext).
:::

<strong>Arguments:</strong> <br></br>

- <code>self</code> [<strong> table </strong>]: The class instance.
- <code>character</code> [<strong> character </strong>]: The Character of the Player that is looking at this Character.

<strong>Returns:</strong> <br></br>

- [<strong> bool </strong>]: A boolean indicating whether the character can be interacted with or not. Defaults to true if <code>client_onInteract</code> is implemented, otherwise false.

---

### onEvent

```lua
function CharacterClass.client_onEvent( self, event )
end
```
Called when a [Player](/lua/Game-Script-Environment/Userdata/Player) is interacting with the [Character](/lua/Game-Script-Environment/Userdata/Character) by pressing the <code>Use</code> key (default <code>E</code>).

Called when the [Character](/lua/Game-Script-Environment/Userdata/Character) receives an event from [Player:sendCharacterEvent](/lua/Game-Script-Environment/Userdata/Player#sendcharacterevent) or [Unit:sendCharacterEvent](/lua/Game-Script-Environment/Userdata/Unit#sendcharacterevent).

This is usually for triggering animations on the character.

For more extensive events, see [sm.event.sendToCharacter](/lua/Game-Script-Environment/Static-Functions/sm.event#sendtocharacter).

<strong>Arguments:</strong> <br></br>

- <code>self</code> [<strong> table </strong>]: The class instance.
- <code>event</code> [<strong> string </strong>]: The event.

---