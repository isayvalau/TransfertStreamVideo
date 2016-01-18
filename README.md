#TUTORIAL STREAMING VIDEO



I.	Sending and retrieving the video stream

To send the video stream, we have downloaded a free app on the first smartphone named “IP Webcam”. This app is available on Google Play. The app permits to use the camera of the smartphone and to transform it into a camera IP.
In fact, by launching the application you can see your video stream just by reaching its IP address and its port from any Web browser. 
You can see above the app launched on the smartphone with at the bottom of the screen the IP Address where the stream is available.
 
Then go on a Web Browser, write the IP Address and the port (example: http://192.168.0.101:8080) and you’ll see the stream.
 

 	

II.	Displaying the video stream in an Android activity

Normally, to display a video stream in an Android activity, a videoview must be used. However, this widget only supported some video formats such as H.263, H.264 AVC, MPEG-4 S or VP8.
The video stream which is sent by the app isn’t really a video. It’s a stream of a lot of pictures, so we need to convert this stream in a real video stream.
For this, you must to import in your Android project two Java classes of treatment (MjpegView and MjpegInputStream) and you’ll have to create a new class in a second part.

One they are added, we’re going to use the Mjpegview class to create a widget which will permit you to display the video in the activity. 
So, you must add a Mjpegview in your activity layout.


Then, you have to declare it in your MainActivity and to use the method findViewByID to retrieve it in the user interface because you need to interact with programmatically.

Now, we’re going to create the class which will permit to create a HTTP Client and to initiate the connection with it. The class must slip from AsyncTask because the connection will be made in an asynchronous way.
But AsyncTask must be subclassed to be used. The subclass will override at least one method (doInBackground(Params...)), and most often will override a second one (onPostExecute(Result).)

We have to associate this class to the object mVideo in the MainActivity and we execute the asynchronous task with an entry parameter which is the URL of the stream.

I’m just going to explain you the role of the class named MjpegInputStream. This class extends from “java.io.DataInputStream”.
It permits to wrap the given input stream, internal buffers are automatically created.
The method in this class named “readMjpegFrame()” permits to read the next MjpegFrame from the stream and it returns a Bitmap.
In fact, this function is called in the class MjpegView to draw bitmaps thanks to “drawBitmap()”. 

You can download the complete project on GitHub.
