# ⛏ UEFN Verse Style Guide
### A guide to help developers to write better understandable verse code.

This style guide has the main objective to suggest how Verse codes are implemented, improving the visibility and code maintenance.

# 1. Code formatting
## 1.1. CamelCase or snake_case?
Variable names and identifiers must be in **CamelCased** instead of the usual **snake_case**.
This is because CamelCase is shorter and simpler to view. Of course, UEFN's native classes are in snake_case, but using CamelCase differentiates our code from theirs.
Also, think of the variable Agent (with a capital A), without a complement, writing agent (with a lowercase a) makes the compiler think we are referring to the agent type. 
So by keeping the CamelCase standard we avoid a lot of confusion with what is already ready in UEFN.


Examples:

**Right**
```c++
PlayerSpawnerDevice : player_spawner_device = player_spawner_device{}
var DamageAmount : int = 0

OnBegin()<suspends> : void=
  PlayerSpawnerDevice.SpawnedEvent.Subscribe(OnPlayerSpawned)

OnPlayerSpawned(Agent : agent) : void=
  if (FortChar := Agent.GetFortCharacter[]):
    Print("Killing player")
    FortChar.Damage(100.0) 
```
**Wrong**
```c++
player_spawner:player_spawner_device=player_spawner_device{}
var my_var:int=0

OnBegin()<suspends>:void=
  player_spawner.SpawnedEvent.Subscribe(player_spawned_event)

player_spawned_event(agent_spawned:agent):void=
  if (fort_char:=agent_spawned.GetFortCharacter[]):
    Print("Killing player")
    FortChar.Damage(100.0)
```

## 1.2. English, Portuguese or Spanish?
Let's agree!! It would be much easier if everything was in our own language, wouldn't it?
However, you must also recognize that in the world of programming, especially the commands for the languages we use, are written in English.
So think about the mess the code turns into by mixing English with Portuguese and Spanish. No one will be able to understand.
Let's establish that the standard language for coding our devices is International **ENGLISH**.
You will be able to work for everyone using English as code base language.

Examples:

**Right**
```c++
PlayerSpawnerDevice : player_spawner_device = player_spawner_device{}
var DamageAmount : int = 0

OnBegin()<suspends> : void=
  PlayerSpawnerDevice.SpawnedEvent.Subscribe(OnPlayerSpawned)

OnPlayerSpawned(Agent : agent) : void=
  if (FortChar := Agent.GetFortCharacter[]):
    Print("Killing player")
    FortChar.Damage(DamageAmount)
```

**Wrong**
```c++
SpawnerJogador:player_spawner_device=player_spawner_device{}
var DanoCausado:int=0

OnBegin()<suspends>:void=
  SpawnerJogador.SpawnedEvent.Subscribe(AoJogadorEntrar)

AoJogadorEntrar(Agente:agent):void=
  if (pergonagem:=Agente.GetFortCharacter[]):
    Print("Matando o jogador")
    personaegm.Damage(DanoCausado)
```

## 1.3. Spacing
Spacing must be added to separate operators and symbols in order to have better visibility of the code inside. The Verse in Visual Studio Code inserts templates without proper spacing, however it's important to change them so when we "take a look", we can quickly understand the elements that are part of the syntax.

Examples:

**Right**
```c++
PlayerSpawnerDevice : player_spawner_device = player_spawner_device{}
var DamageAmount : int = 0

OnBegin()<suspends> : void=
  PlayerSpawnerDevice.SpawnedEvent.Subscribe(OnPlayerSpawned)

OnPlayerSpawned(Agent : agent) : void=
  if (FortChar := Agent.GetFortCharacter[]):
    Print("Killing player")
    FortChar.Damage(DamageAmount)
```

**Wrong**
```c++
PlayerSpawnerDevice :player_spawner_device = player_spawner_device{}
var DamageAmount:int=0
var UnusedVariable: int= 0

OnBegin()<suspends>:void=
  PlayerSpawnerDevice.SpawnedEvent.Subscribe(OnPlayerSpawned)

OnPlayerSpawned(Agent:agent):void=
  if(Fortchar:=Agent.GetFortCharacter[]):
    Print("Killing player")
    FortChar.Damage(DamageAmount)
```

## 1.4. Declaration order
TBD

# 2. Naming variables and functions
The naming of variables and functions should suggest what they do (in the case of functions) or what type of data it stores (in the case of variables). Correctly naming variables and functions allows us to understand what a block of code does without the need to fill it with comments, polluting the code.

## 2.1. Variables
In some cases, it is interesting while naming a variable to say what the meaning of its existence is, for example, suppose we have a Boolean variable (logic) that defines whether a prop should be shown or not. Therefore, it is preferable to insert the preposition Is before it so that it is possible to quickly see that that variable is Boolean.
See that in the example below the name PlayerSpawnerDevice was used for the player_spawner_device. It could be Player1SpawnerDevice or Player2SpawnerDevice, but understand that this way, the Game Designer, if necessary, can access the managing device and find the correct Spawner, as the name already indicates which type of data should be referenced.
We can also adopt this practice for other visual elements of the editor such as Props (PropMachineLevel1, PropMachineLevel2, PropHeroStatue, PropVillainStatue and so on).

Examples:

**Right**
```c++
@editable
PlayerSpawnerDevice : player_spawner_device = player_spawner_device{}
@editable
PropHeroStatue : creative_prop = creative_prop{}
@editable
PropVillainStatue : creative_prop = creative_prop{}
@editable
var IsShowingHeroStatue : logic = false

OnBegin()<suspends> : void=
  PlayerSpawnerDevice.SpawnedEvent.Subscribe(OnPlayerSpawned)

OnPlayerSpawned(Agent : agent) : void=
  if (not IsShowingHeroStatue?):
    set IsShowingHeroStatue = true
    PropHeroStatue.Show()
```

**Wrong**
```c++
@editable
PlayerSpawner : player_spawner_device=player_spawner_device{}
var MyVar : int = 100.0
@editable
hero_1 : creative_prop = creative_prop{}
@editable
villain:creative_prop=creative_prop{}
@editable
HeroVisible : logic = false

OnBegin()<suspends>:void=
  PlayerSpawner.SpawnedEvent.Subscribe(OnPlayerSpawned)

OnPlayerSpawned(Agent:agent):void=
  if(HeroVisible = false):
    hero_1.Show()
```

2.2. Functions

TBD
