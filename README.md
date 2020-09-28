# Android-Basics

1. Main components of Android:
	Activities - Activity represents an UI
	Intents - Go from one activity to another, Start a service and send a broadcast 
	Services - Don't have UI, runs in background,(Ex: Download task)
	Broadcast Receivers - Register to listen for system events or custom events and it performs its taks as specified, Ex: Custom Braodcast Receiver (Download Complete Message) or System Event (Battery Low Message)
	Content providers - Provides the content necessary to another app Ex:Whatsapp asks for contacts and Contacts app provides the content

2. How Android understands which Layout to be shown?
	manifest.xml - Entry point for all application
	Android OS looks for the manifest and searches intent-filter with ACTION.VIEW
	Activity onCreate
	UI Set content view
	Inflate the layout

3. Activity lifecycle:
	
	ACTIVITY LAUNCHED
	onCreate() - created
	onStart() - visible, not useable 
	onResume() - usable
	ACTIVITY RUNNING
	onPause() - another activity comes shadows our activity
	onStop() - is not visible (when activity is running again it calls onRestart() and it goes to onStart())
			if memory is high os kills our activity and if restarted it goes to onCreate()
	onDestroy() - closed
	ACTIVITY DESTROYED

4. Intents:
	Facilitates communication between components
	a) Start an Activity
	b) Start a Service
	c) Delevering a Broadscast
	Types:
	a) Impplicit Intent (if activity from 1 app calls activity from another app)
	b) Explicit Intent (if another activity is called within same app)	

5. Manifest:
	Provides essential info about our app
	Package name
	App version code and version name
	Min and Max supported sdk versions
	Icon, Theme, App name
	Permissions
	Activities
	Services

6. Material design:
	Introduced Lollipop version
	Widgets, shadows, vector drawable, animation
	Listview Recyclerview and cardview

7. Diff between list and recyclerview:
	The RecyclerView is much more powerful, flexible and a major enhancement over ListView
	Recycles the same view and doesn't create new views like listview
	ViewHolder pattern is used in RecyclerView, each time it doesn't ahve to call findViewById() for mapping the text view inside list
	Listview supports only linear layout, Recyclerview supports LinearLayoutManager, StaggeredLayoutManager, GridLayoutManager
	Item animation, item decoration, onItemTouchListener
	RecyclerView prepares view just ahead and behind the visible entries
	Performance is dramatically faster, especially if you use RecyclerView.setHasFixedSize

8. Fragments:
	A portion of UI displayed on an Activity
	Statically using Layout Xml
	Dynamically using FragmentManager
	Lifecycle of an Activity is the lifecycle of fragment

9. Fragment Classes:
	DialogFragment
	ListFragment
	PreferenceFragment
	Single FrameFragment

10. Thread:
	To run a process beside the main process
	We con't control the process in thread and doesn't gives progress of the task so we use Async Task

11. Async Tasks:
	Can achieve multithreading
	Can update the main UI
	Methods:
	onPreExecute
	doInBackgraound
	onUpdateProgress
	onPostExecute
	Parameters:
	Params - parameters sent to task for execution
	Progress - progress units of the task
	Result - result of the task
	Async disadvantage is taht we have to maintain seperate thread, creating, destroying, cache management
12. Loaders:
	Loads data from content providers and other data source
	Loaders simplify thread management
	Starts on a seperate thread by default
	
 
