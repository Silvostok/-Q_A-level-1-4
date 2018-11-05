# Android Development Course - Q/A level 1-4 
Miguel Rubio, Caballero ID1S3, 
Stud.nr.: 50013052

Level 1
## 1	 What is the name of the newest version of Android?
Android versie 9 (API level 28)

## 2	In which Java file are the ID resources defined?
activity_main.xml 
content_main.xml
 
## 3	What is ART?
Android runtime (ART) is the managed runtime used by applications and some system services on Android. ART and its predecessor Dalvik were originally created specifically for the Android project. ART as the runtime executes the Dalvik Executable format and Dex bytecode specification.

## 4	In which resource directory are images stored?
Folder -> drawable

## 5	Describe the difference between constraint layout and relative layout?
 [ConstraintLayout](https://developer.android.com/reference/android/support/constraint/ConstraintLayout.html)  allows you to create large and complex layouts with a flat view hierarchy (no nested view groups). It’s similar to  [RelativeLayout](https://developer.android.com/reference/android/widget/RelativeLayout.html)  in that all views are laid out according to relationships between sibling views and the parent layout, but it’s more flexible than RelativeLayout and easier to use with Android Studio’s Layout Editor.

## 6	Why do we need density-independent pixels?
* [Support different pixel densities  |  Android Developers](https://developer.android.com/training/multiscreen/screendensities)
Not only do Android devices come in  [different screen sizes](https://developer.android.com/training/multiscreen/screensizes.html)  (handsets, tablets, TVs, and so on), but their screens also have different pixel sizes. That is, while one device has 160 pixels per square inch, another device fits 480 pixels in the same space. If you don’t consider these variations in pixel density, the system might scale your images (resulting in blurry images) or the images might appear at the completely wrong size.
The first pitfall you must avoid is using pixels to define distances or sizes. Defining dimensions with pixels is a problem because different screens have different pixel densities, so the same number of pixels may correspond to different physical sizes on different devices.
To preserve the visible size of your UI on screens with different densities, you must design your UI using _density-independent pixels_ (dp) as your unit of measurement. One dp is a virtual pixel unit that’s roughly equal to one pixel on a medium-density screen (160dpi; the “baseline” density). Android translates this value to the appropriate number of real pixels for each other density.

## 7	 What are the differences between Toast and Snackbar?
**Toast:**
Android also provides a capsule-shaped toast, primarily used for system messaging. Toasts are similar to snackbars but do not contain actions and cannot be swiped off screen.

A toast provides simple feedback about an operation in a small popup. It only fills the amount of space required for the message and the current activity remains visible and interactive. Toasts automatically disappear after a timeout.

1 Toast was added in API Level 1
2 Basically Activity is not required (Can be shown on Android home or even above other apps)
3 It can’t perform an action based on User input
4 It can’t be dismissed by swiping
5 It can’t handle user input like Swipe, Click etc.
6 Good for showing info messages to user

**SnackBar:**
Snackbars provide lightweight feedback about an operation in a small popup at the base of the screen on mobile and at the lower left on desktop. They are above all over elements on screen, including the FAB.

Snackbars provide lightweight feedback about an operation. They show a brief message at the bottom of the screen on mobile and lower left on larger devices. Snackbars appear above all other elements on screen and only one can be displayed at a time.
They automatically disappear after a timeout or after user interaction elsewhere on the screen, particularly after interactions that summon a new surface or activity. Snackbars can be swiped off screen.

1 SnackBar was added in API Level 23
2 It can be showed inside an activity of the Applications
3 It can perform an action
4 It can be dismissed by swiping
5 It can handle user input
6 Good for showing warning/info type messages to user that needs attention
**Usage of SnackBar and Toast:**
**SnackBar:**
SnackBar can be used in the areas where a simple popup message needs to be displayed along with an option to perform action. For Example: In GMail application, when you delete Mail, quick SnackBar display at the bottom with Message ‘1 Deleted’ with an action button ‘Undo’. On pressing the ‘Undo’ action button, the deleted mail will be restored.
**Toast:**
Toast can be used in the areas where System messages need to be displayed.
For Example:
When your App tries to download JSON from remote server but it fails due to Server Timeout or No resource found, you just need to display the error message saying that ‘Error Occurred’. But understand the Toast message cannot be dismissed by swiping. If you still want to have the capability of dismissing it in your App, go for SnackBar.

## 8	What is the meaning of “this” in next code example:
```
mAdapter= new ArrayAdapter<>(this, android.R.layout.simple_list_item_1, mReminders);
```

This is used to reference a member of the current class

- - - -

# Level 2
## 1	Explore this app:  [https://github.com/marcellis/demorecyclerview](https://www.google.com/url?q=https://github.com/marcellis/demorecyclerview&sa=D&ust=1537202703673000)  and explain why recyclerview is called “recycler”*

Recycle (view): A view previously used to display data for a specific adapter position may be placed in a cache for later reuse to display the same type of data again later. This can drastically improve performance by skipping initial layout inflation or construction.

## 2	What is the difference of a staggered grid comparing to a normal grid?
staggered grid - 
A LayoutManager that lays out children in a staggered grid formation. It supports horizontal & vertical layout as well as an ability to layout children in reverse.
Staggered grids are likely to have gaps at the edges of the layout. To avoid these gaps, StaggeredGridLayoutManager can offset spans independently or move items between spans. You can control this behavior via  [setGapStrategy(int)](https://developer.android.com/reference/android/support/v7/widget/StaggeredGridLayoutManager.html#setGapStrategy(int)) .

normal grid - 

## 3	 What is the purpose of logcat?
Logcat is a command-line tool that dumps a log of system messages, including stack traces when the device throws an error and messages that you have written from your app with the  [Log](https://developer.android.com/reference/android/util/Log.html)  class.

Android Logcat is a part of the Android **monitoring toolbox** and an adb (Android Debug Bridge) sub-command. Any developer can thus get all logs and messages from their remote (or emulated) device. Android Logcat allows you to: View, filter and collect all application logs.

## 4	 Would you use logcat developing Android apps? Why or why not?
Log has impact on performance. Excessive logging impacts device and application performance. At a minimum, debug and verbose logging should be used only for development purposes and removed prior to application publication.
- - - -

# Level 3 Questions
## 1	Explore this app:  [https://github.com/marcellis/demolifecycle](https://www.google.com/url?q=https://github.com/marcellis/demolifecycle&sa=D&ust=1537809387140000)  and examine which lifecycle events are fired navigating from one activity to the other.
MainActivity: calling toNextActivity from MainActivity
MainActivity: calling onCreate from NextActivity
MainActivity: calling onStart from NextActivity

## 2	 What is the difference between implicit and explicit intents?
An  [Intent](https://developer.android.com/reference/android/content/Intent.html)  is a messaging object you can use to request an action from another  [app component](https://developer.android.com/guide/components/fundamentals.html#Components) . Although intents facilitate communication between components in several ways, there are three fundamental use cases:

**Starting an activity**
**Starting a service**
**Delivering a broadcast**

There are two types of intents:
* **Explicit intents** specify which application will satisfy the intent, by supplying either the target app’s package name or a fully-qualified component class name. You’ll typically use an explicit intent to start a component in your own app, because you know the class name of the activity or service you want to start. For example, you might start a new activity within your app in response to a user action, or start a service to download a file in the background.
* **Implicit intents** do not name a specific component, but instead declare a general action to perform, which allows a component from another app to handle it. For example, if you want to show the user a location on a map, you can use an implicit intent to request that another capable app show a specified location on a map.

## 3 	What is the difference between Parcelables and Serializables?*
Passing primitive data types like string, integer, float, etc. through intents is quite easy in Android. All you have to do is put the data with unique key in intents and send it to another activity. If a user wants to send Java objects through intent, Java class should be implemented using the Parcelable interface. Serialization, on the other hand, is a Java interface that allows users to implement the interface which gets marked as Serializable.
During the Android application development process, developers often have to send Java class objects from one activity to another activity using the intent. Developers can opt from the two types of object passing techniques, i.e. Serialization and Parcelable of object.  The fact that Parcelable is faster than Serialization makes it a preferred choice of approach while passing an object. Here’s why:
**Implementation**
Android Parcelable implementation allows objects to read and write from Parcels which can contain flattened data inside message containers.
If a developer wants to convert a Java object into Parcelable, then the best way to do so is by implementing the Parcelable interface and overriding the writeToParcel() methods in its own class. The first step is to override the writeToParcel() method and  write all object members into parcel objects. The second is to create a static Parcelable.Creator object to de-serialize the Java object.
**Differences between Serialization and Parcelable**
Parcelable and Serialization are used for marshaling and unmarshaling Java objects.  Differences between the two are often cited around implementation techniques and performance results. From my experience, I have come to identify the following differences in both the approaches:
· Parcelable is well documented in the Android SDK; serialization on the other hand is available in Java. It is for this very reason that Android developers prefer Parcelable over the Serialization technique.
· In Parcelable, developers write custom code for marshaling and unmarshaling so it creates less garbage objects in comparison to Serialization. The performance of Parcelable over Serialization dramatically improves (around two times faster), because of this custom implementation.
· Serialization is a marker interface, which implies the user cannot marshal the data according to their requirements. In Serialization, a marshaling operation is performed on a Java Virtual Machine (JVM) using the Java reflection API. This helps identify the Java objects member and behavior, but also ends up creating a lot of garbage objects. Due to this, the Serialization process is slow in comparison to Parcelable.

## 4 	What is the purpose of the analyzer?
Android Studio includes an APK Analyzer that provides immediate insight into the composition of your APK after the build process completes. Using the APK Analyzer can reduce the time you spend debugging issues with DEX files and resources within your app, and help reduce your APK size. It’s also available from the command line with  [apkanalyzer](https://developer.android.com/studio/command-line/apkanalyzer.html) .
- - - -


# Level 4 
## 1 	A singleton pattern is used in the class that defines the database. What is the purpose of this pattern?
A singleton is intended to provide only one instance of itself while facilitating a global point of access. Implementing a singleton pattern involves creating a class with a method that creates a new instance of the class. In order to implement a singleton pattern, principles of single instance and global access must be satisfied. The singleton class is like a global repository for an instance of itself, making the constructor private. Therefore, an instance outside the class cannot be created at all, and a singleton can contain only one instance. A singleton class instantiates itself and maintains that instance across systems. 

## 2 	Why should you load the data in a background thread?

Background processing in Android refers to the execution of tasks in different threads than the **Main Thread**, also known as **UI Thread**, where views are inflated and where the user **interacts** with our app.


## 3 	Why should you use breakpoint to debug your app?
Android Studio supports several types of breakpoints that trigger different debugging actions. The most common type is a line breakpoint that pauses the execution of your app at a specified line of code. While paused, you can examine variables, evaluate expressions, then continue execution line by line to determine the causes of runtime errors.


## 4 	How can you extract the current database so that you can see the table, columns and its data?
In an active emulator, select View -> Tool Windows -> Device File Explorer. Find data -> data -> <project name> -> databases; export (right-click) the 3 files. Open with an Sql browser and view the data.

- - - -

