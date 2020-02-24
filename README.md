# OpenCV_task
Used OpenCV to read frame by frame video stream through websocket using python.

#Reading a Video
In OpenCV, a video can be read either by using the feed from a camera connected to a computer or by reading a video file. The first step towards reading a video file is to create a VideoCapture object. Its argument can be either the device index or the name of the video file to be read.

In most cases, only one camera is connected to the system. So, all we do is pass ‘0’ and OpenCV uses the only camera attached to the computer. When more than one camera is connected to the computer, we can select the second camera by passing ‘1’, the third camera by passing ‘2’ and so on.

#Created a VideoCapture object and read from input file
# If the input is taken from the camera, pass 0 instead of the video file name.
 
cap = cv2.VideoCapture('ws://1.2.3.4:8888')



#Displaying a video
After reading a video file, we can display the video frame by frame. A frame of a video is simply an image and we display each frame the same way we display images, i.e., we use the function imshow().

As in the case of an image, we use the waitKey() after imshow() function to pause each frame in the video. In the case of an image, we pass ‘0’ to the waitKey() function, but for playing a video, we need to pass a number greater than ‘0’ to the waitKey() function. This is because ‘0’ would pause the frame in the video for an infinite amount of time and in a video we need each frame to be shown only for some finite interval of time, so we need to pass a number greater than ‘0’ to the waitKey() function. This number is equal to the time in milliseconds we want each frame to be displayed.

While reading the frames from a webcam, using waitKey(1) is appropriate because the display frame rate will be limited by the frame rate of the webcam even if we specify a delay of 1 ms in waitKey.

While reading frames from a video that you are processing, it may still be appropriate to set the time delay to 1 ms so that the thread is freed up to do the processing we want to do.

In rare cases, when the playback needs to be at a certain framerate, we may want the delay to be higher than 1 ms.

#Writing a video

After we are done with capturing and processing the video frame by frame, the next step we would want to do is to save the video.

For images, it is straightforward. We just need to use cv2.imwrite(). But for videos, we need to toil a bit harder. We need to create a VideoWriter object. First, we should specify the output file name with its format (eg: output.avi). Then, we should specify the FourCC code and the number of frames per second (FPS). Lastly, the frame size should be passed.
