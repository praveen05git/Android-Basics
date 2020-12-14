# Android-Basics

<b>1. Main components of Android:</b>
* Activities - Activity represents an UI
* Intents - Go from one activity to another, Start a service and send a broadcast 
* Services - Don't have UI, runs in background,(Ex: Download task)
* Broadcast Receivers - Register to listen for system events or custom events and it performs its taks as specified, Ex: Custom Braodcast Receiver (Download Complete Message) or System Event (Battery Low Message)
* Content providers - Provides the content necessary to another app Ex:Whatsapp asks for contacts and Contacts app provides the content</br>

<b>2. How Android understands which Layout to be shown?</b>
* manifest.xml - Entry point for all application
* Android OS looks for the manifest and searches intent-filter with ACTION.VIEW
* Activity onCreate
* UI Set content view
* Inflate the layout

<b>3. Activity lifecycle:</b>
	
* ACTIVITY LAUNCHED
* onCreate() - created
* onStart() - visible, not useable 
* onResume() - usable
* ACTIVITY RUNNING
* onPause() - another activity comes shadows our activity
* onStop() - is not visible (when activity is running again it calls onRestart() and it goes to onStart())
			if memory is high os kills our activity and if restarted it goes to onCreate()
* onDestroy() - closed
* ACTIVITY DESTROYED

<b>4. Intents:</b>
* Facilitates communication between components
	* Start an Activity
	* Start a Service
	* Delevering a Broadscast
* Types:
	* Impplicit Intent (if activity from 1 app calls activity from another app)
	* Explicit Intent (if another activity is called within same app)	

<b>5. Manifest:</b>
* Provides essential info about our app
* Package name
* App version code and version name
* Min and Max supported sdk versions
* Icon, Theme, App name
* Permissions
* Activities
* Services

<b>6. Material design:</b>
* Introduced Lollipop version
* Widgets, shadows, vector drawable, animation
* Listview Recyclerview and cardview

<b>7. Difference between list and recyclerview:</b>
* The RecyclerView is much more powerful, flexible and a major enhancement over ListView
* Recycles the same view and doesn't create new views like listview
* ViewHolder pattern is used in RecyclerView, each time it doesn't ahve to call findViewById() for mapping the text view inside list
* Listview supports only linear layout, Recyclerview supports LinearLayoutManager, StaggeredLayoutManager, GridLayoutManager
* Item animation, item decoration, onItemTouchListener
* RecyclerView prepares view just ahead and behind the visible entries
* Performance is dramatically faster, especially if you use RecyclerView.setHasFixedSize

<b>8. Fragments:</b>
* A portion of UI displayed on an Activity
* Statically using Layout Xml
* Dynamically using FragmentManager
* Lifecycle of an Activity is the lifecycle of fragment

<b>9. Fragment Classes:</b>
* DialogFragment
* ListFragment
* PreferenceFragment
* Single FrameFragment

<b>10. Thread:</b>
* To run a process beside the main process
* We con't control the process in thread and doesn't gives progress of the task so we use Async Task

<b>11. Async Tasks:</b>
* Can achieve multithreading
* Can update the main UI
* Methods:
	* onPreExecute
	* doInBackground
	* onUpdateProgress
	* onPostExecute
* Parameters:
	* Params - parameters sent to task for execution
	* Progress - progress units of the task
	* Result - result of the task
* Async disadvantage is that we have to maintain seperate thread, creating, destroying, cache management
	
<b>12. Loaders:</b>
* Loads data from content providers and other data source
* Loaders simplify thread management
* Starts on a seperate thread by default

<b>13. Services:</b>
* https://www.geeksforgeeks.org/services-in-android-with-example/#:~:text=Playing%20music%20in%20the%20background,order%20to%20pause%20the%20music.
* https://www.tutorialspoint.com/android/android_services.htm
	
<b>14. Important Questions:</b>
- https://www.toptal.com/android/interview-questions
 
<b>15. Work Manager:</b>
- WorkManager aims to simplify the developer experience by providing a first-class API for system-driven background processing. It is intended for background jobs that should run even if the app is no longer in the foreground. Where possible, it uses JobScheduler or Firebase JobDispatcher to do the work; if your app is in the foreground, it will even try to do the work directly in your process.
- https://medium.com/google-developer-experts/services-the-life-with-without-and-worker-6933111d62a6
- WorkManager — receives work with arguments & constraints and enqueue it.
- Worker — have only one method to implement doWork() which is executed on a background thread. It’s the place where all your background tasks should be done. Try to keep it as simple as possible.
- WorkRequest — work request specify which Worker enqueued with what Arguments and what are the Constraints for it (e.g., internet, charging ).
- WorkResult — Success, Failure, Retry.
- Data — Persistable set of key/value pairs which are passed to/from Worker

- Extend the class and define the work
```
public class LocationUploadWorker extends Worker {
    ...
     //Upload last passed location to the server
    public WorkerResult doWork() {
        //do the work
        return WorkerResult.SUCCESS;
    }
}
```
- Execute the work
```
WorkManager.getInstance().enqueue(uploadWork);
```
- Observe the work
```
WorkManager.getInstance().getStatusById(locationWork.getId()).observe(this,
        workStatus -> {
    if(workStatus!=null && workStatus.getState().isFinished()){
         ...
    }
});
```
<b>16. Intent Flags:</b>
- <b>FLAG_ACTIVITY_NEW_TASK -</b> If set, this activity will become the start of a new task on this history stack. A task (from the activity that started it to the next task activity) defines an atomic group of activities that the user can move to. Tasks can be moved to the foreground and background; all of the activities inside of a particular task always remain in the same order.

- <b>FLAG_ACTIVITY_CLEAR_TOP -</b> If set, and the activity being launched is already running in the current task, then instead of launching a new instance of that activity, all of the other activities on top of it will be closed and this Intent will be delivered to the (now on top) old activity as a new Intent.

- <b>FLAG_ACTIVITY_SINGLE_TOP -</b> If set, the activity will not be launched if it is already running at the top of the history stack.
