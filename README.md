# **TrafficOverSpeedReporting**

### **DESCRIPTION:** 
##### Code takes traffic video feed, detect vehicles and analyzes it's speed. If vehicle overspeeds(speed limit = 60 KMPH), it captures vehicles image, and tries to detect vehicle number plate and stores the same in dataframe.


### **ISSUES:** 
##### The video used as input has low resolution, so model was unable to detect number plates of overspeeding vehicles.

### **DETAILED EXPLANATION:**

#### Code is divided in three parts: Vehicle Detection & Tracking, Analyse Speed, Detecting number plate for overspeeding vehicles

##### Vehicle Detection & Tracking:
> Grabbing frames from input video(cars.mp4) using opencv2.
> Using Haarcascade classifier(myhaar.xml: pretrained model on images of vehicles from the rear) to detect vehicles.
> Assigning ids to vehicles using corelation tracker from dlib library

##### Analyse Speed:
> Calculating the distance moved by the tracked vehicle in a second in terms of pixels, so we need pixel per meter(PPM) to calculate the distance travelled in meters.
> PPM value varies on input video and needs to be adjusted as per input.
> With distance travelled per second in meters, we get the speed of the vehicle:

##### Detecting number plate for overspeeding vehicles:
> If vehicle overspeeds(SPEED LIMIT = 60 KMPH), cropping the vehicle box area from frame and saving it to process number plate.
> Converting vehicle image from RGB to Grayscale, detecting edges and contours to grab number plate image area.
> Using Pytesseract to get number plate in string form from grabbed number plate image area.
