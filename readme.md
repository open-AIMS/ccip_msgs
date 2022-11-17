# CCIP MSGS
ROS message types used for detecting objects in a series of images. 
Objects will be tracked through the image sequence.
Initially used for detecting Crown-of-thorns Starfish (COTS) and COTS scars.

The intent is that a node would subscribe to topic of type sensor/Image or similar.
If any object of interest is detected it should publish to a topic of type ccip_msgs/FrameDetections.
One message of type FrameDetections will relate to one Image.
The Image should be identified by the header field which will appear in both messages (Image and Frame Detections).

The FrameDetection contains an array of SequencedDetection; 
one for each object detected in that image.
SequencedDetection/length is the length of the sequence so far.
If the object is seen again in the next photo, the length will be incremented.

SequencedDetection has a detection which contains a bounding box and an array of DetectionResult.

DetectionResult has a class_id (initially COTS or SCAR) and a probability that it is object. 
The reason for the array is because the system might say something like 
30% likely to be COTS and 40% likely to be SCAR.




