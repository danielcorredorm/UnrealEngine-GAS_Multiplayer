<!-- DRAFT for github.com/danielcorredorm/UnrealEngine-GAS_Multiplayer — not part of the website build.
     Copy it to the repo root as README.md (it replaces the one-line Spanish title).
     Everything here was read from the repo's own source and config. -->

# GAS multiplayer — course project (Unreal Engine 4.25, C++)

[![Gameplay video](https://img.youtube.com/vi/8h8SWPf-Ca4/hqdefault.jpg)](https://youtu.be/8h8SWPf-Ca4)

A small third-person multiplayer battle game built on the Gameplay Ability System, made while following the course *Multiplayer Video Game Development in Unreal Engine* (Arkde, 2021). It is course work, not an original design: I share it as a sample of GAS and replication code I have written.

**More projects:** https://danielcorredorm.dev/projects/

## What is in it

| System | Where | What it shows |
|---|---|---|
| Ability base and attributes | [`Abilities/Core`](Source/ArkdeCM/Public/Abilities/Core) | Base `UGameplayAbility` and `UGameplayEffect` classes; a replicated attribute set with Health, Mana and Stamina, each with Max and Regen, and current values adjusted when a max changes |
| Montage ability task | [`ACMT_PlayMontageAndWaitForEvent`](Source/ArkdeCM/Public/Abilities/Core/ACMT_PlayMontageAndWaitForEvent.h) | Custom `UAbilityTask` that plays a montage and waits for gameplay events |
| Abilities | [`Abilities/`](Source/ArkdeCM/Public/Abilities) | Fire Bolt (projectile), Magic Shield, Run (stamina cost through a gameplay effect), Shocking Grasp (absorption sphere) and Wind Swirl (wind sphere) |
| Storm | [`Enviroment/ACM_Storm`](Source/ArkdeCM/Private/Enviroment/ACM_Storm.cpp) | Server-only overlap: leaving the safe area applies a damage gameplay effect, coming back in removes it |
| Pickups | [`Objects/`](Source/ArkdeCM/Public/Objects) | Collectables and a spawner that creates them |
| Sessions and lobby | [`Core/ACM_GameInstance`](Source/ArkdeCM/Private/Core/ACM_GameInstance.cpp), [`Core/ACM_LobbyGameMode`](Source/ArkdeCM/Private/Core/ACM_LobbyGameMode.cpp) | Two-player sessions; the lobby counts players and seamless-travels to the battle map once enough have joined |
| RPCs | [`Character/ArkdeCMCharacter`](Source/ArkdeCM/Public/Character/ArkdeCMCharacter.h), [`FireBolt/ACM_Projectile`](Source/ArkdeCM/Public/Abilities/FireBolt/ACM_Projectile.h) | Client RPCs that push health, mana and stamina changes to the owning player's UI; a server death RPC with a multicast death; multicasts on the ability actors |

## Build and play

1. Unreal Engine **4.25** and Visual Studio with the C++ game development workload.
2. Right-click `ArkdeCM.uproject` → **Generate Visual Studio project files**, build **Development Editor | Win64**, then open the project.
3. The game starts on `SessionMap`; the editor opens on `BattleRoyalMap`. Abilities are on keys 1–4, sprint on Left Ctrl, jump on Space.

## Notes

- Course project: the structure and systems follow the course.
- Content includes marketplace and Epic sample assets (Paragon characters and others) used for the course.
- No license: the source is shared to read and study; all rights reserved.

## Contact

Daniel Corredor — Senior Gameplay Engineer, Unreal Engine · [Portfolio](https://danielcorredorm.dev) · [LinkedIn](https://www.linkedin.com/in/danielcorredorm2787)
