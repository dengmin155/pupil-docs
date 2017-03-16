+++
date = "2017-01-19T12:24:57+07:00"
title = "capture data"
section_weight = 1
page_weight = 1
+++

## Capture Data

Download and install the Pupil Capture application bundle. Put on the Pupil headset and plug it into your computer. Open the Pupil Capture app. You will be presented with 2 windows – `World` and `Eye`.

Work through the following steps to get familiar with the Pupil workflow. You can also check out [video tutorials](#walkthrough-videos) at the end of the guide. 

<!-- Dive deeper in the [user guide](https://github.com/pupil-labs/pupil/wiki/User-Guide). -->

### 1. Pupil Hardware
Put on and plug in your Pupil headset. Headsets are adjustable and shipped with additional parts. For more information head over to the [Pupil Hardware](#pupil-hardware) guide.

### 2. Start the Pupil Capture App
If headset is plugged in and detected, `World` and `Eye` windows will open and display the real-time video.

<p align="center">
  <img src="https://raw.githubusercontent.com/wiki/pupil-labs/pupil/media/basic-workflow/pupil-capture/icon/pupil-capture-pointer.png" width="20%">
</p>

### 3. Intro to the UI
Below are the two main windows we will interface with throughout the application.

**World Window**
Let's get familiar with the `World` window.

<p align="center">
  <img src="https://raw.githubusercontent.com/wiki/pupil-labs/pupil/media/basic-workflow/world-callout.png" width="80%">
</p>

The `World` window is the main control center for `Pupil Capture`. It  displays a real-time video feed of your field of view (FOV), camera controls for the world view, controls for plugins like calibration, recording, streaming, and more.

  1. **Graphs** - this area contains performance graphs. You can monitor `CPU` and `FPS` as well as the `Confidence` of the pupil detection algorithm.  
  1. **Sidebar** - The main GUI for the `World` window is a sidebar. Click the `<|` icons to expand sidebar and sub-menus and  `|||` to collapse. The sidebar is scrollable. Plugins will launch new sub-menus in the sidebar.
  1. **Gaze dot** - the red dot shows where you are looking within the `world` FOV.
  1. **Hot keys** - this area contains clickable buttons for plugins. Letters correspond to keyboard shortcuts. Example: press the `C` key to start calibrating or press the `R` key to start/stop recording.

Let's take a closer look at the `General` sub-menu.

<p align="center">
  <img src="https://raw.githubusercontent.com/wiki/pupil-labs/pupil/media/basic-workflow/world-sidebar-callout.png" width="40%">
</p>

1. **Detection and mapping mode** - you can select `2d` or `3d` detection and mapping mode. We recommend 3d mode for almost all use cases.
1. **Detect eye0** and **Detect eye1** - these toggled buttons launch and stop eye processes in a new `Eye` window. All settings you make will be saved for the next time `Pupil Capture` is opened.
1. **Open plugin** - select a plugin from the drop down list. A plugin sub-menu will be added to the GUI with (optional) hot key. You can make your own plugins. Read more about that [here](#plugin-guide).



**Eye Window**

The `Eye` window displays a real-time video of your eye. You will primarily use the `Eye` window GUI to configure pupil detection algorithm parameters and eye camera settings.  

<img src="https://raw.githubusercontent.com/wiki/pupil-labs/pupil/media/basic-workflow/eye-callout.png" width="100%">

1. **Graph** - this area contains performance graphs. You can monitor `CPU` and `FPS`.
1. **Sidebar** - the main GUI for the `World` window is a sidebar. Click the `<|` icons to expand sidebar and sub-menus and  `|||` to collapse. The sidebar is scrollable. Plugins will launch new sub-menus in the sidebar.
1. **Pupil diameter** - Red circles are visualizations of `pupil min` and `pupil max` diameter. The Green circle is a visualization of the current apparent pupil diameter. Blue number in the center is the current apparent pupil diameter in pixels.

### 4. Pupil Detection
After focusing the eye camera, take a look at the Eye window. If the pupil is detected you will see a red circle around the edge of your pupil and a red dot at the center of your pupil.

If the algorithm's detection confidence is high, the red circle will be opaque. If confidence diminishes the circle will become more transparent.

Try moving your head around a bit while looking at your eye to see that the pupil is robustly detected in various orientations.

**Eye image mode**

There are three modes that you can select from the `General` menu: Camera Image, Region of Interest (ROI), and Algorithm. Here we will discuss Camera Image and Algorithm view mode.

<table>
<tr>
  <th><p align='center'>Camera Image</p></th>
  <th><p align='center'>Algorithm
</tr>
  <tr>
    <td width="50%">
    <img src="https://raw.githubusercontent.com/wiki/pupil-labs/pupil/media/basic-workflow/pupil-hardware/pupil-detection/pupil-camimage2.png" width="100%">
    </td>
    <td width="50%">
    <img src="https://raw.githubusercontent.com/wiki/pupil-labs/pupil/media/basic-workflow/pupil-hardware/pupil-detection/pupil-algorithm.png" width="100%">
    </td>
  </tr>
  <tr>
    <td valign='top'>
    <small>Raw eye camera image. This uses the least amount of CPU power. Red ellipse and red dot are visualizations of the pupil detection algorithm.</small>
    </td>
    <td valign='top'>
    <small>Algorithm mode shows a visualization of the pupil detection algorithm parameters on top of the eye video stream.</p></small>
    </td>
  </tr>
</table>

**Pupil detection algorithm settings**
Switch to `Algorithm` mode so that you can see a visualization of the pupil algorithm parameters set in the GUI.

<table>
  <p align="center"></p>
  <tr>
    <td><img src="https://raw.githubusercontent.com/wiki/pupil-labs/pupil/media/basic-workflow/pupil-capture/eye-ui/pupil-detect-algor.png" width="100%"></td>
    <td><img src="https://raw.githubusercontent.com/wiki/pupil-labs/pupil/media/basic-workflow/pupil-hardware/pupil-detection/pupil-algorithm.png" width="100%"></td>
  </tr>
</table>

* In the `General` menu in the sidebar, switch the `Mode` to `Algorithm`
  * Scroll down to the `Pupil Detector 2D` submenu
  * Adjust `Pupil min` and `Pupil max` sliders.
  * Red circles in the bottom left visualize `Pupil min` and `Pupil max` values.
  * The green circle and value displayed at the center of the circles is the current pupil diameter. Make sure the green circle is within the two red circles.

<aside class="notice">
See <a href="#pupil-capture">Pupil Capture</a> for more details about pupil detector settings and advanced options.
</aside>

### 5. Calibrate
Pupil calibration process establishes the mapping from pupil to gaze coordinates. One or two cameras capture a subject's eye movements - Eye Camera - and another one records the subject's FOV - World Camera. In order to know what someone is looking at -- specifically where their `gaze` or fovea is regarding the word camera space -- we first need to find out how pupil and gaze positions are mapped. This is what we call calibration.

Steps
1. Go to the `World` window.
1. In the `Calibration` sub-menu select `Screen Marker Calibration` as the method.

**Screen Marker Calibration Method**
<table>
  <tr>
    <td width="50%"><img src="https://raw.githubusercontent.com/wiki/pupil-labs/pupil/media/basic-workflow/pupil-capture/recording-directory/record-callout.png" width="100%"></td>
    <td width="50%"><img src="https://raw.githubusercontent.com/wiki/pupil-labs/pupil/media/basic-workflow/pupil-hardware/calibrate/calibrate-border.png" width="100%"></td>
  </tr>
  <tr>
    <td valign='top'>
    <small>Click `c` on the world screen or press `c` on the keyboard to start calibrate.</small>
    </td>
    <td valign='top'>
    <small>Follow the marker on the screen with your eyes and try to keep your head stationary</small>
    </td>
  </tr>  
</table>

There are other calibration methods and lots more information about how calibration works -- read more on [calibration](#calibration).

### 6. Verify Successful Calibration
If the system has been calibrated correctly you will see a message "Calibration Successful". After calibration the red dot will point directly to the current gaze point.

### 7. Record
If calibration is successful, start capturing data.

This means that Pupil Capture will save the world video stream and all corresponding gaze data in a folder.

<p align="center">
  <img src="https://raw.githubusercontent.com/wiki/pupil-labs/pupil/media/basic-workflow/pupil-capture-v07-world-recording.png" width="80%">
</p>

Steps

  * Start recording: Press the `r` key on your keyboard or press the circular 'R' button in the left hand side of the world window.
  * The elapsed recording time will appear next to the 'R' button.
  * Stop recording: Press the `r` key on your keyboard or press the circular 'R' button in the left hand side of the world window.

See a video demonstration of how to set recordings path, session name, and start recording -- [here](http://youtu.be/VzIXFUqv99s).

**Where is the recording saved?**
By default, each recording will live in its own unique data folder contained in the `recordings` folder.

You can make as many recordings as you like. 

<p align="center">
    <img src="https://raw.githubusercontent.com/wiki/pupil-labs/pupil/media/basic-workflow/pupil-capture/recording-directory/recording_folder_v07.png" width="100%">
</p>

The default `recordings` directory will have the following hierarchy.

* `recordings`
  * 2016-04-05
    * 001
    * 002
    * 003
    * ####

**How recordings are saved?**
Pupil capture saves the video frames in a fixed frame rate container. This means that the raw output video (world.mp4) does not show the correct duration and the correct frame rate of the recording. This information can be found in `world_timestamps.npy`, which tells you exactly where each frame belongs in time.

However, if you export using Pupil Player, the video will be made such that the frames will show at the exact right time. The output video will not miss any frame of the raw video, instead, output frames are spaced out exactly as they where initially captured.

<aside class="notice">
Note - The real FPS during recordings may fluctuate due variations on light intensity (LUX, lumens) and other issues; it cannot be forced to be constant.
</aside>