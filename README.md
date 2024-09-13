# Gesture Alteration - GestAlt 

## Using game engine Unity's editor to manipulate a gesturing avatar and provide stimuli for research studies

This reposit houses a Unity package 'GestAlt' with C# scripts and sample files used to manipulate and render avatar animations (gestures) using Unity's Inverse Kinematics (IK) component.

The purpuse is the production of stimuli (video) for multimodal comunication research studies (e.g. on gestures) where you want to present an avatar gesturing for one group and present another avatar with a slightly altered gesture to another group. 

The point in using avatars is to control exactly what to alter - and nothing else. Imposible to acomplish by aranging an actor to perform two acts with only that exclusive difference. 

As the figure below illustrates, the GestAlt pipeline takes care of the necessary steps between a motion capture plus face and/or sound recording and the rendering of a video  with your avatar reproducing these behaviors. The main use of GestAlt is to alter the size of specific manual gestures in the avatar.

![GestAlt pipeline range][def]

### Contact

Do not hesitate to contact the authors with any questions:

- Henrik Garde: henrik.garde@humlab.lu.se
- Valentijn Prové: valentijn.prove@gmail.com

## Scientific paper/book

Methodology developed for a study by Valentijn Prové, KU Leuven (title and reference to be announced) in collaboration with Henrik Garde, Lund University Humanities Lab.

## Aim

The 'GestAlt' Unitiy package is created to provide a graphical user interface (GUI) that allows researchers, novel to programming and 3D modelling, to create variations of animated 3D avatars doing gestures - based on prior motion capture recordings of gestures.

While containing sample recordings of speech, face expression and motion together with a gesture definition file and an avatar fitted to adapt to these data files, the aim is also to provide a training material to try out the 'GestAlt' tool, withut adding anything.

The aim is not to teach the entire workflow including setup of a motion capture studio or modifying a standard avatar to fitt to the sample data. A short description to inspire is included, though.

## Requirements

It only requires a personal Unity license (free) to install and start producing video stimuli for a studie. The effort it takes to record new material for a new avatar is explained briefly here.

### Keywords

avatar, gesture, face expression, visual perception, multimodal speech perception, inverse kinematics 

## Inverse Kinematics (IK)

Unity's build-in model for IK is employed to make the avatars joints (shoulder, arm) follow the alteration of a hand position in a 'natural' way. 

Based on 'target' position and 'weight' parameters (for position and/or rotation) a hand kan then be 'dragged' more or less strongly to a certain 3D point. 

The mathematics behind it is not entirely specified and may be a product of machine learning (??). (Further evaluation/... is outside the scope of the scripts in this deposit).

GestAlt has an interface that allows users to try parameter values while a gesture is looping and hence immediately see how the gesture changes while dragging in sliders. 

This is thought to minimise/solve the difficulties of imaging or knowing how the sum of all settings affects the avatar's gestures.

## Assessment

IK parameters representing alterations of the original avatar's gestures are saved in a text file as documentation and usefull for evaluation and replication. 

## Sample files

This package contains an avatar with animation of full body motion and face expression as well as an audio file for speech. A formated csv file with gestures is needed for the GestAlt tool to work, while describing when a gesture to manipulate starts and stops. The same file is used to save the settings applied in the GestAlt tool. 

Sample output data produced from the sample data using the GestAlt tool is are shared in the Unity project's *Assets* folder. 

1. Motion files: /Assets/fbx/farm_repr_2.fbx 

2. Speech files: /Assets/audio/farm_repr_2.wav

3. Face expression files: /Assets/face_x/f_farm_repr_2.csv

4. Gesture file: /Assets/gesture/g_farm_repr_2.csv

In the scene (or tab Hierarchy), select Game Object: rain_QTM_fbx_prefab to see how the sample files are applied in the Inspector tab.

### Acknowledgement

We gratefully acknowledge Katrien Arron, for allowing us to share data from recordings with this deposit and Lund University Humanities Lab for providing access and expertice to recordings of motion, audio and face expressions in the lab's Motion Capture Studio. 

## Dependencies

Prior to importing the GestAlt pakage, your Unity project (Mac, Linux or Windows) needs to be prepared: 

1. Install Unity 2020.3.22f1

2. Create a new 3D (Core) project and open it 

3. In the Unity Editor in menu: Window, select Package Manager 

4. Install Animation Rigging

5. Install Unity Recorder


Then import the GestAlt package via menu: Assets | Import Package | Custome package...

If the GestAlt tab is not found, select it from menu: Window | GestAlt. 

# Manipulate Gestures

If not already done, select scene 'Rain'. The scene is located in the Project tab in the folder: Scenes, and select by double clicking it.

Press Play (or menu: Edit | Play) to run the project (and enter Play Mode) and the GestAlt tool should appear in a right tab next to the Inspector tab.

The Unity project contains sample data (see above) that allows users to directly alter gestures and render a video based on it. 

## Loop over One or All Gestures

In Play Mode, when the checkbox Repeat Gesture is checkec, the Prev and Next buttons allows to browse through the gestures defined in the sample csv file: Assets/gesture/g_farm_repr_2.csv, which counts twelve gestures named G01 to G12. 

If the repeat Gesture is unchecked, then entire recording will be played from start to end. This mode is usefull when checking the transmission(?) between gestures before rendering a video.

## Select a Gesture to Manipulate

While a selected gesture is repeated (looped) in the Game View it will be updated when the sliders in the GestAlt tool changes. 

The samples gestures are all defined with a start and end time as/when hands are resting in the lap. No garanties that manipulation of any gesture will work if a gesture starts or ends elsewhere.

## Manipulate Sample Gesture Stepwise

The manipulations of two specific gestures, named G06 and G08, are executed as described as 'hands on' procedures in this chaper. 

These example gestures are the only ones with Rig Weight applied.

- G06: The ‘sawing’ gesture

- G08: The 'panicking’ gesture

### Using Arm and Target Rig Weight 

Select gesture G06 using Prev or Next buttons. 

- Set both Rig Weight and Target Weight to 1, while leaving the Target Position at 0.

- Apply the Arm Weight constraint at different degrees in order to see how it is affecting the gesture. 

The arm will still make a movement that is reminiscent of the original mocap recording, even at Weight 1. 

Values between 0.70 and 1 are advised to make gestures visibly smaller, pulling them downward and more towards the body and more in front of the belly (into the center of gesture space area).

The same effect can be obtained by setting the Arm Weight at 1 and reducing the Target Weight.

Adjust the Rotation Weight if the wrist is making an exaggerated movement compared to the arm movement.

### Adding Hint Weight 

Select gesture G08, the ‘panicking’ gesture using Prev or Next buttons.

If the procedure described above for G06 is applied to G08, the elbows fall inward and the movement looks unnatural. 

It suffices to leave the hint at its zero position and gradually apply it. Much like the target position, the hint position is located next to the body so it pulls the elbows outward.

### Changing the Target and Hint Position 

Select gesture G06, the ‘sawing’ gesture. 

GestAlt can also be used to enlarge gestural movement by changing the Target and Hint positions. 

This can either be a goal in itself or a strategy to alter the gesture trajectory if the movement becomes undesired after the standard manipulations. 

In the latter case, the gesture trajectory is first extended towards another part of the gesture space and it is then reduced.

- Set Rig Weight, Target Weight and Hint Weight to 1. Arm Weight remains at 0.

- Change the y-position for both the target and the hint to 0,40. The gesture is making zigzagging movement and we want to make the movement amplitude larger on the vertical axis.

- Set the Arm Weight to a very small value, e.g. 0.01. 

This will activate the influence of the Target and the Hint Weight, while keeping the arm as free as possible.

By increasing the Arm Weight, the gesture space can be reduced. Even in a smaller version of the gesture, the movement trajectory will keep some properties of the exaggerated version pushed by the Target and Hint Weight.

- Adjust the Wrist Rotation.

Repeat for the other arm.

# Manipulate Scene's Light and Camera 

Besides from the Avatar (named rain_QTM_fbx_prefab in the Hierarchy tab), the project Scene contains a Camera (Main Camera), several Light sources (Direct Light, Point Light, Spot Light) and a Background (Canvas). 

All these objects can be modified to make the Avatar appear differently. Select the object of choise in the Hierarchy, then select the Inspector tab and locate the properties to change.

It is recommended to make small changes and watch the result by entering Play Mode (press Play) and repeat that in several steps. Also, save the result in another Scene file via menu: File | Save as... 

The original scene is located in folder /Assets/Scenes/ and any scene can be loaded by double-clicking it via the Project tab inside the Unity editor. 

# Render Scene to Video

Before you render a video to use for stimulus, uncheck the Repeat Gesture checkbox in the GestAlt tab. In Play mode you will see the entire motion file play from start to end in the Game window.

While playing, be sure to have selected the Avatar (rain_QTM_fbx_prefab) in the Hierarchy tab, before going to the Inspector tab and check the Movie Recorder component (a checkbox) wich will enable and start a video rendering of the Game window. 

Uncheck the same Movie Recorder checkbox to stop recording. The output is a mp4 file located in the Project root in the /SampleRecordings/ folder. Notice that video files will be named after the gesture file (e.g., g_farm_repr_2.mp4) and owerwrite any existing mp4 file in this folder.

# Create new Material

Motion recordings for this project are captured with a Qualisys system based on optical markers. Face expression is recorded with a smartphone and the Live Link Face app. Audio with a lapel microphone. All synchronised with a clapper with mocap markers mounted. 

Skeleton data solved from the motion files exported to the fbx format from any motion capture system should work. Some scaling or adjustment of a skeleton template or the avatar rig, may be needed.

[def]: gestalt_concept.png