Author: Grzegorz Heller  
Date: 12.2020  

# Cross_Slide_Apparatus
<p align = "justify"> Cross Slide Apparatus (Polish: Aparat Suportu Krzyżowego) is a device used for testing eye-hand coordination. The examinee operates the device using two cranks. Each crank is responsible for moving the cross slide table in one axis, creating two degrees of freedom. The goal of the examinee is to get from start point to end point of a given trail (on this example the trail is a star) without straying away from the path (the stylus leaving the path counts as an error). The standard solution of this device utilises current flow through stylus upon touching a metal plate with engraved path (a zero-one error measurement). The original idea presented here is to utilise computation to achieve a more detailed image of examinee's ability. The image below shows the top view of the device.</p>

<p align = "center"> <img src = "images/top.jpg" align = "middle" /> </p>

<p align = "justify"> The image below shows a 2D rendering of a 3D model of the cross slide table made in Fusion 360. Shafts responsible for table movement in X and Y axis are placed on ball bearings. The stylus is mounted on a special arm and points more or less to the middle of a closed cross slide table. Section F shows a close up of a carved out wood. This is a mounting place for a handmade rotary encoder assembled from two optocouplers. A windmill-shaped material can be seen in the same position on the first image. This material is attached to the shaft and rotates with it in the same direction, blocking and letting through infrared emitted by a diode depending on the angular position of the shaft. One rotary encoder consists of two optocouplers (to distinguish the direction of rotation of the shaft), a windmill attached to the shaft and a special interrupt routine on the MCU. Using two such encoders (one for each axis) allows calculation of the position of the stylus (relative to a certain manually determined starting point) in XY plane. Knowing the trail (star) width and the diameter of the stylus we can use this information to calculate when and for how much and how long did the examinee stray from the correct path. This original solution, while possesing a certain unspecified error (due to the manual setting of starting point, for example) provides far more data, which can be used to asses the examinee's ability, than the standard Cross Slide Apparatus version utilizing current flow.</p>

<p align = "center"> <img src = "images/drawing.jpg" align = "middle" /> </p>

<p align = "justify"> Images of a freshly assembled cross slide table.</p>

<p align = "center"> <img src = "images/table1.jpg" align = "middle" /> </p>
<p align = "center"> <img src = "images/table2.jpg" align = "middle" /> </p>

<p align = "justify"> Images of a PCB designed in Eagle. Buzzer is used to signalise start and end of a test. End of a test is signalised automatically when the stylus reaches the ending position. Diodes sygnalise which state the device is actually in (state machine). Bluetooth module is used to communicate with an Android device in order to transfer relevant data.</p>

<p align = "center"> <img src = "images/pcb_bottom.png" align = "middle" /> </p>
<p align = "center"> <img src = "images/pcb_top.png" align = "middle" /> </p>

<p align = "justify"> The device is completely controlled via an Android application over Bluetooth (except for a reset button present on the PCB). Android application sends to the MCU commands such as connect, disconnect, start a test, choose a trail (star or snake), send data and clear data to prepare for a new test. The data collected by the device are (from top left to bottom right): time of the whole test, total time when the stylus was outside of the correct path (error state), the total distance travelled by the stylus in an error state, the maximum distance away from path in the whole test, number of errors, the longest time the stylus stayed in a single error state before returning to correct path. In addition the MCU sends the current position of the stylus, so that the Android application can draw the travelled path (red colour).</p>

<p align = "center"> <img src = "images/app.jpg" align = "middle" /> </p>

<p align = "justify"> The application generates two files when the report button is pressed. One is a text file with all necessary data, the other is an image of the travelled path.</p>

<p align = "center"> <img src = "images/report.png" align = "middle" /> </p>

<p align = "justify"> The accuracy of the prototype could be improved for example by utilising better production technology (cross slide table, encoders, paths, etc.), or by designing a better way of setting a starting point.</p>
