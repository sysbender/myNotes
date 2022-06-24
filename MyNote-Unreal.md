- [1. MyNote-Unreal](#1-mynote-unreal)
- [2. reference](#2-reference)
  - [2.1. shaders](#21-shaders)
- [3. myNote-UnrealShader](#3-mynote-unrealshader)
- [4. reference](#4-reference)
- [5. official document - Understanding the basic of UE](#5-official-document---understanding-the-basic-of-ue)
  - [5.1. installing](#51-installing)
  - [5.2. fondation knowledge](#52-fondation-knowledge)
    - [5.2.1. UE Editor interface](#521-ue-editor-interface)
    - [5.2.2. UE Terminology](#522-ue-terminology)
    - [5.2.3. Tools and Editors](#523-tools-and-editors)
    - [5.2.4. Corordinate Space Terminology](#524-corordinate-space-terminology)
    - [5.2.5. Guide for games](#525-guide-for-games)
    - [5.2.6. Guide for Non-Games](#526-guide-for-non-games)
  - [5.3. content browser](#53-content-browser)
  - [5.4. customizing unreal engine](#54-customizing-unreal-engine)
  - [5.5. projects and templates](#55-projects-and-templates)
    - [create a custom template](#create-a-custom-template)
    - [upgrade UE4 project to UE5](#upgrade-ue4-project-to-ue5)
    - [template reference](#template-reference)
    - [project setting](#project-setting)
  - [5.6. levels](#56-levels)
  - [5.7. assets and Content Packs](#57-assets-and-content-packs)
  - [5.8. Actors and Components](#58-actors-and-components)
  - [5.9. Playing and Simulating](#59-playing-and-simulating)
  - [5.10. Building Your Application](#510-building-your-application)
- [6. learn basic of unreal](#6-learn-basic-of-unreal)
  - [6.1. map is level](#61-map-is-level)
- [7. Crash Course: An Introduction to Unreal Engine](#7-crash-course-an-introduction-to-unreal-engine)
  - [7.1. unreal project structure](#71-unreal-project-structure)
  - [7.2. projects](#72-projects)
  - [7.3. levels](#73-levels)
  - [7.4. actor](#74-actor)
  - [7.5. components and UI](#75-components-and-ui)
  - [7.6. viewports](#76-viewports)
  - [7.7. importing meshes](#77-importing-meshes)
  - [7.8. Quixel Bridge](#78-quixel-bridge)
  - [7.9. datasmith mesh importing](#79-datasmith-mesh-importing)
  - [7.10. static mesh editor](#710-static-mesh-editor)
  - [7.11. mesh guidelines](#711-mesh-guidelines)
  - [7.12. collision mesh](#712-collision-mesh)
  - [7.13. lightmap UVs](#713-lightmap-uvs)
  - [7.14. textures : mipmaps](#714-textures--mipmaps)
  - [7.15. PBR makes life easier](#715-pbr-makes-life-easier)
  - [7.16. PBR core properties](#716-pbr-core-properties)
  - [7.17. common PBR usage](#717-common-pbr-usage)
- [8. packet beginner](#8-packet-beginner)
  - [8.1. 05 - create playable character](#81-05---create-playable-character)
    - [8.1.1. 05.01-game_modes.mkv](#811-0501-game_modesmkv)
    - [8.1.2. 05.02-pawns.mkv](#812-0502-pawnsmkv)
    - [8.1.3. 05.03-characters.mkv](#813-0503-charactersmkv)
- [9. unreal - learn cpp make games](#9-unreal---learn-cpp-make-games)
  - [9.1. importing bull cow game](#91-importing-bull-cow-game)
  - [9.2. view port control](#92-view-port-control)

# 1. MyNote-Unreal

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
 
 ## 2.1. shaders
 # 3. myNote-UnrealShader


# 4. reference

虚幻4渲染编程 - https://zhuanlan.zhihu.com/p/36630694

延迟渲染 Deferred Rendering https://blog.csdn.net/poem_qianmo/article/details/77142101


unreal rendering pass :
https://unrealartoptimization.github.io/book/profiling/passes/



https://blog.csdn.net/u010281174/article/details/123806725


# 5. official document - Understanding the basic of UE

## 5.1. installing

UE5 new feature requirement
* Lumen Global Illumination and Reflections - ray trace
* Nanite Virtualized Geometry
* Virtual Shadow Maps
* Temporal Super Resolution

## 5.2. fondation knowledge

### 5.2.1. UE Editor interface

* select mode - editing : select, Landscape, Foliage, Mesh, Fracture, Brush  
* level ViewPort - Perspective, Ortographic
* command   console, source control status
* outline : hider/reveal , create folder
### 5.2.2. UE Terminology
* project
* blueprint
* object -UObject, gc, Uproperty
* class - Blueprint, Gameplay
* Actor - AActor, can be placed
* Casting - 
* conponent
* Pawn - 
* Charactor - 
* PlayerController
* AIController
* Player state
* Game Mode
* Game state
* Brush
* Volume - blocking volume, pain causing volume, trigger volume
* level
* world
* 
### 5.2.3. Tools and Editors
* level editor
* static mesh editor - look , collision, UV Mapping, LODs
* Material Editor
* Blueprint Editor
* Physics Asset Editor - Physics for Skeletal Meshes
* Behavior Tree Editor - AI behavior
* Niagara Editor - Particle effect 
* UMG UI Editor - user interface
* Font Editor
* Sequencer Editor - Cinematics and Dynamic Events
* Animation Editor - Skeleton  asset/mesh, Animation Blueprint
* Control Rig Editor
* sound cue Editor
* Media editor
* nDisplay 3D config editor
* DMX Libvrary Editor
* 
### 5.2.4. Corordinate Space Terminology

Coordinate spaces
* Tangent - right/left handed, 
* Local /Object space
* World
* TranslatedWorld
* View/CameraSpace
* Clip , HomogeniousCoordinates, PostProjectionSpace, ProjectionSpace
* Screen / OpenGL NormalizedDeviceCoordinates
* viewPort , ViewportCoordinates, WindowCoordinates
* 
### 5.2.5. Guide for games
compiling code projects:

targets:  - *.target.cs
* editor
* client
* game
* server

build configuration : state + target
* Debug - debug engline and game code
* DebugGame - debug game code only
* Development - is the default,  enables all but the most time-consuming engine and game code optimizations
* shipping
* Test -  the Shipping configuration with some console commands, state, profiliing tool enabled

Build configuration : target only
* [empty] - standalone executable
* Editor - open a project in  Unreal Editor
* Client - <game>Client.Target.cs
* Server - <game>Server.Target.cs



### 5.2.6. Guide for Non-Games






## 5.3. content browser

## 5.4. customizing unreal engine
* plugin
* keboard shortcuts
* editor preference

## 5.5. projects and templates

### create a custom template
Custom templates can include 
* content  
* settings 
* code 
* have specific plugins enabled or disabled by default.

steps to create custom template from existing project:
* copy project folder to  C:\Program Files\Epic Games\UE_[version]\Templates
* add or update projectName in [ProjectName]\Config\DefaultGame.ini file
* copy existing  Templates\TP_FirstPerson\Config\. Copy the TemplateDefs.ini
  * update LocalizedDisplayNames and LocalizedDescriptions variables
  * set a category : Gmes, ME, AEC, MFG
    * Games - Games
    * ME - Film, Television, and Live Events
    * AEC - Architecture, Engineering, and Construction
    * MFG - Automotive, Product Design, and Manufacturing
* add an icon and preview image in [ProjectName]\Media
    * icon: [ProjectName].png
    * preview : [ProjectName]_Preview.png
### upgrade UE4 project to UE5
1. open the old project in UE5, select "open a copy"

### template reference
* configure input for character(pawn)
  * Edit > Project setting > Engine > Input > Binding 

### project setting
 in engine.ini
Project3rdPerson\Saved\Config\WindowsEditor
* Project category
  * description
  * Maps and Modes - load which map or mode by default
* Engine category
  * input - keybinds in game , not in editor

## 5.6. levels

## 5.7. assets and Content Packs

## 5.8. Actors and Components
 

## 5.9. Playing and Simulating


## 5.10. Building Your Application


 # 6. learn basic of unreal 
 
 ## 6.1. map is level
 
 # 7. Crash Course: An Introduction to Unreal Engine 
 
 ## 7.1. unreal project structure
 ## 7.2. projects
 ## 7.3. levels
 ## 7.4. actor
 ## 7.5. components and UI
 ## 7.6. viewports
 ## 7.7. importing meshes
 ## 7.8. Quixel Bridge
 ## 7.9. datasmith mesh importing
 ## 7.10. static mesh editor
 ## 7.11. mesh guidelines
 ## 7.12. collision mesh
 ## 7.13. lightmap UVs
 ## 7.14. textures : mipmaps
 ## 7.15. PBR makes life easier
 ## 7.16. PBR core properties
 ## 7.17. common PBR usage
 
 

# 8. packet beginner

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

## 8.1. 05 - create playable character
### 8.1.1. 05.01-game_modes.mkv
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


### 8.1.2. 05.02-pawns.mkv
pawns - an actor that can be controlled by human or computer

bludprint class -> Pawn -> 
* add staticMesh to DefaultSceneRoot 
* add a springArm component - auto ajust camera, 
* attach a camera to StaticMesh




### 8.1.3. 05.03-characters.mkv
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



# 9. unreal - learn cpp make games

##  9.1. importing bull cow game
1. unzip the kit zip file
2. double click to launch the game

## 9.2. view port control

