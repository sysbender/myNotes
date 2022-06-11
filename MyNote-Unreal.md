# 1. MyNote-Unreal

- [1. MyNote-Unreal](#1-mynote-unreal)
- [2. reference](#2-reference)
- [3. packet beginner](#3-packet-beginner)
  - [3.1. 05 - create playable character](#31-05---create-playable-character)
    - [3.1.1. 05.01-game_modes.mkv](#311-0501-game_modesmkv)
    - [3.1.2. 05.02-pawns.mkv](#312-0502-pawnsmkv)
    - [3.1.3. 05.03-characters.mkv](#313-0503-charactersmkv)
- [4. unreal - learn cpp make games](#4-unreal---learn-cpp-make-games)
  - [4.1. importing bull cow game](#41-importing-bull-cow-game)
  - [4.2. view port control](#42-view-port-control)
- [5. Unreal Engine C++ Project setup from Scratch](#5-unreal-engine-c-project-setup-from-scratch)
  - [5.1. project structure layout](#51-project-structure-layout)
  - [5.2. module entry file](#52-module-entry-file)
  - [5.3. build](#53-build)
  - [5.4. cook content](#54-cook-content)
  - [5.5. create our own build script](#55-create-our-own-build-script)
- [The Unreal Engine Game Framework : From main() to BeginPlay](#the-unreal-engine-game-framework--from-main-to-beginplay)


# 2. reference

best tutorial with code and blog:
https://github.com/orfeasel/UE4-Cpp-Tutorials


nice post precess effect - https://www.youtube.com/watch?v=lGlB7vL2ifw
7zip plugin - https://github.com/getnamo/ZipUtility-Unreal
intro to plugin - https://michaeljcole.github.io/wiki.unrealengine.com/An_Introduction_to_UE4_Plugins/

Plugin Development in Unreal Engine - https://www.benteveo.kiwi/blog/advanced-unreal-engine-tutorial-part-1

pbr material - https://www.youtube.com/watch?v=AeOQZWEi1gU&t=128s


custom shader node - https://medium.com/@biq/configuring-unreal-engine-for-custom-shader-development-biq-cf79f72e7137


https://www.raywenderlich.com/57-unreal-engine-4-custom-shaders-tutorial

UE4 render programming - https://www.zhihu.com/column/c_187975189


github:
 build automation - https://github.com/botman99/ue4-unreal-automation-tool#Unreal-Automation-Tool
 session automation - https://github.com/DaedalicEntertainment/ue4-test-automation
 
 
 test blog:
 https://zompidev.blogspot.com/2019/06/unreal-engine-4-automation-tests-new-api.html
 
 https://github.com/zompi2/UE4NewAutomationTests
 
 

# 3. packet beginner

01.01-introduction.mkv
01.02-registration_and_installation.mkv
01.04-levels.mkv
01.05-actors.mkv
02.01-level_editor_overview.mkv
02.02-select_editing_mode.mkv
02.03-viewport_i-navigating_within_the_viewport.mkv
02.04-viewport_ii-moving_rotating_and_scaling.mkv
02.05-viewport_iii-snapping.mkv
02.06-viewport_iv-different_ways_to_view_your_level.mkv
02.07-content_browser_i-overview_and_finding_content.mkv
02.08-content_browser_ii-adding_importing_and_saving.mkv
02.09-content_browser_iii-the_settings_menu.mkv
02.10-details_panel_i-details_panel_interface.mkv
02.11-details_panel_ii-the_transform_category.mkv
03.02-brushes.mkv
03.04-lights.mkv
03.05-atmosphere_and_clouds.mkv
03.06-player_start.mkv
03.07-components.mkv
03.08-volumes.mkv
03.09-tutorial_1-creating_the_sky.mkv
03.10-tutorial_2-creating_the_playing_area.mkv
03.11-tutorial_3-building_the_inner_structures_of_the_level.mkv
04.01-introduction_to_blueprints.mkv
04.02-variables.mkv
04.04-flow_control_i.mkv
04.05-flow_control_ii.mkv
04.06-accessing_actors_within_the_level_blueprint.mkv
04.07-timelines.mkv
04.09-tutorial_4-building_the_elevator_platform.mkv
04.10-tutorial_5-creating_the_enemies.mkv
04.11-tutorial_6-creating_a_rotating_door.mkv

## 3.1. 05 - create playable character
### 3.1.1. 05.01-game_modes.mkv
an anctor that can be used to define or force game set rule 
lives, can be paused , time limits, 
-> create blueprint class, "game mode base"

* properties
    * action tick
    * classes 
        * default pawn classes 
        * HUD - text overlays  (health, lives, scores, timer)
    * game mode
        * start players as Spectators - and then spawn manually
        * 

* set default gamemode
-> menu -> edit-> project settings -> maps and modes -> Default GameMode
* override gamemode in each level
setting -> world settings -> GameMode override


### 3.1.2. 05.02-pawns.mkv
pawns - an actor that can be controlled by human or computer

bludprint class -> Pawn -> 
* add staticMesh to DefaultSceneRoot 
* add a springArm component - auto ajust camera, 
* attach a camera to StaticMesh




### 3.1.3. 05.03-characters.mkv
a pawn that has by peddle movement - move by legs

bluePrint class Charachater
* capsule
    * arrow - face
    * mesh
    * charactor movment




    
    
05.04-controllers.mkv
05.05-input_mapping.mkv
05.06-tutorial_7-creating_a_playable_character.mkv
06.01-collisions_i-collision_volumes.mkv
06.02-collisions_ii-collision_events.mkv
06.03-collisions_iii-causing_damage_due_to_collisions.mkv
06.04-tutorial_8-adding_a_damage_system_to_the_game.mkv
06.05-tutorial_9-creating_the_orb_item.mkv
07.01-umg_overview.mkv
07.02-root_widget.mkv
07.03-canvas_panel.mkv
07.04-horizontal_box_and_vertical_box.mkv
07.05-grid_panel_and_uniform_grid_panel.mkv
07.06-common_widget_properties.mkv
07.08-text_widget.mkv
07.09-button_widget.mkv
07.10-border_widget_and_image_widget.mkv
07.11-progress_bar_widget.mkv
07.12-check_box_widget.mkv
07.13-scale_box_and_size_box.mkv
07.14-tutorial_10-creating_the_hud.mkv
07.15-tutorial_11-damage_tint_and_collect_item_tint.mkv
07.16-tutorial_12-restrict_door_opening_and_creating_a_pause_menu.mkv
07.17-tutorial_13-game_over_and_win_screen_menus.mkv
08.01-audio_i-audio_overview_and_sound_waves.mkv
08.02-audio_ii-sound_cues.mkv
08.03-audio_iii-attenuation.mkv
08.04-audio_iv-importing_and_converting_audio.mkv
08.05-tutorial_14-adding_audio_to_the_game.mkv
09.01-downloading_content_from_the_epic_games_launcher.mkv
09.02-importing_3d_objects_from_the_internet.mkv
09.03-packaging.mkv
09.04-tutorial_15-packaging_the_game.mkv
01.03-projects.mkv
02.12-world_outliner.mkv
03.01-static_meshes.mkv
03.03-materials.mkv
04.03-functions.mkv
04.08-blueprint_classes.mkv
07.07-visual_designer.mkv



# 4. unreal - learn cpp make games

##  4.1. importing bull cow game
1. unzip the kit zip file
2. double click to launch the game

## 4.2. view port control

# 5. Unreal Engine C++ Project setup from Scratch

## 5.1. project structure layout

* source/
  * DireCore.Build.cs
    ```
        PublicDependencyModuleNames:
        - Core
        - CoreUObject
        - Engine
    ```
  * Private/
    * DirkCore.cpp
    * TestActor.cpp
  * Public/
    * DirkCore.h
    * TestActor.h
  * DirkEditor.Target.cs
    ```
        ExtraModuleNames:        
        - "DirkCore"
    ```

  * UnrealBuildTool.exe
    * UnrealHeaderTool.exe
    * cl.exe
    * link.exe
  * Intermediate/
    * Build/UE4Editor/
      * Inc/DirkCore/
        * DirkCore.init.gen.cpp
        * TestActor.gen.cpp
        * TestActor.generated.h
      * Development/DirkCore/
        * DirkCore.Cpp.obj
        * DirkCore.init.gen.cpp.obj
        * TestActor.cpp.obj
        * TestActor.gen.cpp.obj
      * Win64/
        * UE4Editor-DirkCore.dll
        * UE4Editor-DirkCore.pdb
  * Dirk.uproject
  ```
    {
        FileVersion: 3,
        EngineAssociation: 4.25,
        Category: "",
        Description: "",
        "Modules":[
            {
                Name: DirkCore,
                Type: Runtime,
                LoadingPhase: Default
            }
        ]

    }
  ```
  


  editor will load the dll module and open the project;
  * name the project : Dirk
  * create a workspace directory : 
  * create a project directory:
    * Dirk
      * ".UProject" - file descript the project
        * "DirkCore" - source module name
          * "Private\"
          * "Public\"
          * "DirkCore.build.cs"
      * "Dirk.Target.cs" - target rule definition, which source module to build the project
      * "DirkEditor.Target.cs" - target rule for Editor, TargetType=Editor
      * "Source\"
        * "DirkCore" - module directory
        * DirkCore.build.cs - module build rule


## 5.2. module entry file

cpp and head file with same name as the module
* registry the module as the primary module of our game:
    ```
    IMPLEMENT_PRIMARY_GAME_MODULE( FDefaultGameModuleImpl, ProjectR, "ProjectR" );
    ```
## 5.3. build
* build.bat - engine/Build/BatchFiles - call UnrealBuildTool.exe
    ```
        # editor target
    ```
      * target : DirkEditor
      * platform: Win64
      * build Configuration : Development (Between debug and shipping)
      * path of uproject
      * -waitnutext -NoHotReload
    * non editor target
    ```
        #no editor target
        target = Dirk
    ```
* start Editor
    ```
       UE4Editor.exe Dirk.uproject -log 

       UE4Editor.exe Dirk.uproject -game -log -windowed -resx=1280 -resy=720 
       # without loading editor, can run console command
    ```
* project setting
  * generate - project ID
  * save a map and set default map


* run game
  * editor version -editor target ; need the full unreal installation
  * standalone verion - no editor target; 

## 5.4. cook content

uncooked - when import an image, get Texture2D asset as .uasset file
cooked - DXT-compressed image 


* to cook
  * run the command line version of editor and pass 
  * the result is in saved\cook
  ```
    UE4Editor-cmd.exe Dirk.uproject -run=cook -targetplatform=WindowNoEditor
  ```
    * UE4Editor-cmd.exe
    * project file
    * cook commandlet
    * target = WindowsNoEditor
  * run game 
  ```
    Dirk.exe -log -windowed -resx=1280 -resy=720
  ```
  
## 5.5. create our own build script

* set vars = vars.bat
    
```batch
@echo off
REM get script directory
set ROOTDIR=%~dp0  
REM strip the trailing slash
set ROOTDIR=%ROOTDIR:~0,-1%
set PROJECT=Dirk
set PROJECT_DIR=%ROOTDIR%\%PROJECT%
set UPROJECT_PATH=%PROJECT_DIR%\%PROJECT%.uproject

set UE4_DIR=E:\Epic Games\UE_4.25
set UE4EDITOR_EXE=%UE4_DIR%\Engine\Binaries\Win64\UE4Editor.exe
set BUILD_BAT=%UE4_DIR%\Engine\Build\BatchFiles\Build.bat

```

* script to build
```batch
call %~dp0\vars.bat

call "%BUILD_BAT%" %PROJECT%Editor Win64 Development "%UPROJECT_PATH%" -waitmutext -NoHotReload
```
* script to run editor
```batch
call %~dp0\vars.bat

REM forward argument to editor
start "" "%UE4EDITOR_EXE%" "%UPROJECT_PATHS" %*
```

 
# The Unreal Engine Game Framework : From main() to BeginPlay


