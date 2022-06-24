# MyNote-Unreal

# reference

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
 
 # learn basic of unreal 
 
 ## map is level
 
 # Crash Course: An Introduction to Unreal Engine 
 
 ## unreal project structure
 ## projects
 ## levels
 ## actor
 ## components and UI
 ## viewports
 ## importing meshes
 ## Quixel Bridge
 ## datasmith mesh importing
 ## static mesh editor
 ## mesh guidelines
 ## collision mesh
 ## lightmap UVs
 ## textures : mipmaps
 ## PBR makes life easier
 ## PBR core properties
 ## common PBR usage
 
 

# packet beginner

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

## 05 - create playable character
### 05.01-game_modes.mkv
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


### 05.02-pawns.mkv
pawns - an actor that can be controlled by human or computer

bludprint class -> Pawn -> 
* add staticMesh to DefaultSceneRoot 
* add a springArm component - auto ajust camera, 
* attach a camera to StaticMesh




### 05.03-characters.mkv
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



# unreal - learn cpp make games

##  importing bull cow game
1. unzip the kit zip file
2. double click to launch the game

## view port control

