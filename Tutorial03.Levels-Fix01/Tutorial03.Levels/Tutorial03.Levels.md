# Tutorial 03 - Levels

- [Overview](#overview)
- [Setup](#setup)
   - [Prefabs](#prefabs)
      - [Levels](#levels)
- [Visual Scripting](#visual-scripting)
   - [Application Variables](#application-variables)
   - [Configuration.Resources](#configurationresources)
   - [Level.PlayTime Object Variable](#levelplaytime-object-variable)
   - [Method.Main.SpawnLevel](#methodmainspawnlevel)
   - [Configuration.Main.LevelSelect](#configurationmainlevelselect)
   - [Method.Main.ResetGameData](#methodmainresetgamedata)
   - [State.Main.LevelSelect](#statemainlevelselect)
   - [State.Main.Level.Intro](#statemainlevelintro)
   - [State.Main.Level.Play](#statemainlevelplay)
   - [State.Main.Level.Outro](#statemainleveloutro)
   - [Finish](#finish)

# Overview

This tutorial serves as a starting point for spawning and destroying levels upon level select.

# Setup

## Prefabs

### Levels

1. Create an empty GameObject in the scene and call it Level1 and make it a prefab by dragging it into a folder Assets->Resources->Prefabs->Levels

    [![img.png](Images/img.png)](Images/img.png)

2. Delete the Level1 GameObject out of the scene.

    [![img_1.png](Images/img_1.png)](Images/img_1.png)

3. You can double click the Level1 Prefab to open it and add any GameObjects you want. Including backgrounds, Sprites, Spawners etc. We will get into Spawners in a later tutorial.

    [![img_2.png](Images/img_2.png)](Images/img_2.png)

# Visual Scripting

## Application Variables

Add the `SelectedLevel` and `ElapsedLevelTime` application variables.

[![img_18.png](Images/img_18.png)](Images/img_18.png)

[![img_19.png](Images/img_19.png)](Images/img_19.png)

## Configuration.Resources

Create a configuration in the Common folder called `Configuration.Resources`

[![img_11.png](Images/img_11.png)](Images/img_11.png)

[![img_12.png](Images/img_12.png)](Images/img_12.png)

## Level.PlayTime Object Variable

1. When opened, add a Variables Component to the Level1 Prefab and add a PlayTime Object Variable.

   [![img_13.png](Images/img_13.png)](Images/img_13.png)

1. Create a folder called "Level" under the main visual scripting folder.

   [![img_14.png](Images/img_14.png)](Images/img_14.png)

2. Create a Object Variable getter.

   [![img_15.png](Images/img_15.png)](Images/img_15.png)

3. Modify the Object.Get.Level.PlayTime to take a GameObject Data Input to can grab the value of play time off of the level we will spawn later.

   [![img_21.png](Images/img_21.png)](Images/img_21.png)

## Method.Main.SpawnLevel

Create a new Method `Method.Main.SpawnLevel`

[![img_10.png](Images/img_10.png)](Images/img_10.png)

[![img_9.png](Images/img_9.png)](Images/img_9.png)

## Configuration.Main.LevelSelect

In the previously created `Configuration.Main.LevelSelect` script graph. Change the Level1ButtonName Key to `LevelButtonName` and change the string literal to `Level`.

[![img_3.png](Images/img_3.png)](Images/img_3.png)

## Method.Main.ResetGameData

Initialize the ElapsedLevelTime Application Variable in the `ResetGameData` method.

[![img_20.png](Images/img_20.png)](Images/img_20.png)

## State.Main.LevelSelect

1. Fix the Level Select click event and set the match rule to Visual Element Name Contains.

[![img_5.png](Images/img_5.png)](Images/img_5.png)

[![img_4.png](Images/img_4.png)](Images/img_4.png)

2. Set the `SelectedLevel` application variable to the visual element name. 

[![img_8.png](Images/img_8.png)](Images/img_8.png)

## State.Main.Level.Intro

Spawn the level and set the spawned level ApplicationSceneVariables.SpawnedLevel to the spawned level.

[![img_17.png](Images/img_17.png)](Images/img_17.png)

## State.Main.Level.Play

Add the functionality to wait for the PlayTime of the spawned level and transition to the outro state.

[![img_22.png](Images/img_22.png)](Images/img_22.png)

## State.Main.Level.Outro

Cleanup the spawned level by destroying it and transition back to the level select.

[![img_23.png](Images/img_23.png)](Images/img_23.png)

## Finish

You should now be able to create any number of levels and spawn them based on the level select screen by creating more level buttons and level prefabs. 