<b>1. onClick:</b></br>
```
btn_save.setOnClickListener(new View.OnClickListener() {
@Override
 public void onClick(final View v) {  }
 }
```
<b>2. Notification:</b></br>
```
Snackbar.make(view,"Enter content", Snackbar.LENGTH_SHORT).show();
Toast.makeText(getApplicationContext(),"Enter content",Toast.LENGTH_SHORT).show();
```

<b>3. Check Permission:</b></br>
```
String permission = Manifest.permission.WRITE_EXTERNAL_STORAGE;
public boolean checkPermission(String permission)
{
  ActivityCompat.requestPermissions(MainActivity.this,new String[]{Manifest.permission.WRITE_EXTERNAL_STORAGE},1);
        int check= ContextCompat.checkSelfPermission(this,permission);
        return (check== PackageManager.PERMISSION_GRANTED);
}
```

<b>4. Intent:</b></br>
To Other Activity:
```
Intent HomeIntent=new Intent(this,HomeScreen.class);
            HomeIntent.putExtra("nitVal","One");
            startActivity(HomeIntent);
            overridePendingTransition(R.anim.right_enter,R.anim.left_out);
Receive Extra:
Intent intent=getIntent();
        String pass=intent.getStringExtra("nitVal");            
To URL:            
Intent playStore = new Intent(Intent.ACTION_VIEW, Uri.parse("https://play.google.com/store/apps/details?id=com.jotter.notes"));
                startActivity(playStore);

              or
              
startActivity(new Intent(Intent.ACTION_VIEW, Uri.parse("http://play.google.com/store/apps/dev?id=7031227816779180923")));

To HomeScreen:
Intent ExitIntent=new Intent(Intent.ACTION_MAIN);
                ExitIntent.addCategory(Intent.CATEGORY_HOME);
                ExitIntent.setFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
                startActivity(ExitIntent);
                ```
                
<b>5. AlertDialog:</b></br>
```
 AlertDialog alert_dia1=new AlertDialog.Builder(MainActivity.this).create();
                alert_dia1.setTitle("Remove Ads!");
                alert_dia1.setMessage("Download the Jotter Lite Pro to enjoy Ad-free service!! Download Now?");

                alert_dia1.setButton(AlertDialog.BUTTON_POSITIVE, "Yes", new DialogInterface.OnClickListener() {
                    @Override
                    public void onClick(DialogInterface dialog, int which) {
                        startActivity(new Intent(Intent.ACTION_VIEW, Uri.parse("https://play.google.com/store/apps/details?id=com.jotterpro.notes&hl=en_IN")));
                    }
                });           
                alt_dia.setButton(AlertDialog.BUTTON_NEGATIVE, "No", new DialogInterface.OnClickListener() {
                    @Override
                    public void onClick(DialogInterface dialog, int which) {
                      dialog.cancel();
                    }
                });
                alert_dia1.show();
                ```
                
<b>6. ListView:</b><br>
```
ListView lView;
ArrayList<String> ar = new ArrayList<>();
ar.add(f.getName());
ArrayAdapter<String> fileAdapter = new ArrayAdapter<>(this, android.R.layout.simple_list_item_1, ar);

            lView.setAdapter(fileAdapter);

            lView.setOnItemClickListener(new AdapterView.OnItemClickListener() {
                @Override
                public void onItemClick(AdapterView<?> parent, View view, int position, long id) {
                    fileName = ar.get(position);
                    viewFiles(null);

                }
            });
                
 onItemClick:
 lView.setOnItemLongClickListener(new AdapterView.OnItemLongClickListener() {
                @Override
                public boolean onItemLongClick(AdapterView<?> parent, View view, final int position, long id) { }
            });
            ```
                
<b>7. Menu:</b></br>
```
@Override
public boolean onCreateOptionsMenu(Menu menu)
{
     MenuInflater inflater=getMenuInflater();
     inflater.inflate(R.menu.opt_menu,menu);
     return true;
}

@Override
public boolean onOptionsItemSelected(MenuItem item)
{
    int opt_id=item.getItemId();

    switch (opt_id)
    {
         case R.id.opt_new:
    }
 }
 ```
 <b>8. Manifest:</b></br>
 ```
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<application
android:label="@string/app_name"
android:roundIcon="@mipmap/ic_icon_circle">
<activity android:name=".SplashScreen">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
</activity>
```

<b>9. Bottom Navigation:</b></br>
```
private BottomNavigationView.OnNavigationItemSelectedListener mOnNavigationItemSelectedListener
            =  new BottomNavigationView.OnNavigationItemSelectedListener() {

        @Override
        public boolean onNavigationItemSelected(@NonNull MenuItem item) {

            Fragment fragment=null;

            switch (item.getItemId()) {
                case R.id.weekly:
                    fragment=new weekly_fg();
                    break;
                    }
            return loadFragment(fragment);
        }
    };
    
Load Fragment:    
    private boolean loadFragment(Fragment fragment)
    {
        if(fragment!=null)
        {
            getSupportFragmentManager()
                    .beginTransaction()
                    .setCustomAnimations(R.anim.right_enter, R.anim.left_out)
                    .replace(R.id.fg_container,fragment)
                    .commit();
            return true;
        }
        return false;
    }
    ```

<b>10. Shared Preference:</b></br>
Writing the value:
```
SharedPreferences pref = getContext().getSharedPreferences("ProPref", 0); // 0 - for private mode
SharedPreferences.Editor editor = pref.edit();
editor.putInt("ProPage",3);
editor.apply();
        
Reading the value:
SharedPreferences preferences=getApplicationContext().getSharedPreferences("ProPref",0);
int page=preferences.getInt("ProPage",-1);
```
