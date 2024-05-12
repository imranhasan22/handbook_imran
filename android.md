# View
### TextView

- `android:text` - sets the initial text displayed by the View
- `android:layout_width` or `android:layout_height` - sets the widht and height of the view. Possible values are:
    - `match_parent` - it will set the entire height/width of parent view 
    - `wrap_content`- it will set the space as much as needed
- `android:id` - assigned identifier is used to refer the view in java/kotlin
- `android:textColor` - sets the color of the text.
- `android:textSize` - sets the size of the text.
- `android:visibility` - control the visibility. Possible values are `visible`, `invisible`, `gone`.
- `android:backgroundTint` - 

### ImageView

- `android:src` - specify the image to be displayed
- `android:scaleType` -
- `android:adjustViewBounds` -
- `android:cropToPadding` - 
- `android:clickable` - make an image clickable
- `android:onClick` - specify the method should be invoked when the image is clicked

### EditText

- `android:inputType` - specify the type of the data
- `android:hint` - set placeholder
- `android:text` - set the initial text
- `android:maxLength` - specify the maximum length of the text can be entered
- `android:imeOptions` -
- `android:textCursorDrawble` -
- `clearFocus()` - dismiss the soft keyboard if it's open

### ListView
ListView is a viewgroup that can display a list of scrollable items. Each of the item is clickable
- `android:divider` -
- `android:dividerHeight` -
- `android:dividerSelector` -

List Data Container:
```
<string-array name="list_container">
    <item>Item 1</item>
    <item>Item 2</item>
    <item>Item 3</item>
    <item>Item 4</item>
    <item>Item 5</item>
</string-array>
```

Accessing the data container:
```
String[] items = getResources().getStringArray(R.array.list_container);
```

### Adapter
Adapter pulls the data from the source & convert into a view and then set the view into ListView/GridView/Spinner. Commonly used adapters are:
- Array Adapter - single list item
- Base Adapter - customized list item

```
ListView listView = findViewById(R.id.listView);

String[] countries = {"USA", "Canada", "UK", "Australia", "Germany","France"};

ArrayAdapter<String> adapter = new ArrayAdapter<>(this, android.R.layout.simple_list_item_1, countries);

listView.setAdapter(adapter);
```

Adapter takes three parameters: the context (`this`), the layout for each item (`android.R.layout.simple_list_item_1` is a `built-in layout` provided by Android for a simple list item), and the array of data.
`setAdapter()` populates the ListView with the data provided by the adapter.

# Java Handling
### Eventlistener

- `Button myButton = findViewById(R.id.myButton)` - finds a button with the id `myButton` defined in the layout XML file and assigns it to a variable named myButton.

- `myButton.setOnClickListener(new View.OnClickListener() { ... })` - sets an OnClickListener on the button myButton.

### View Methods

- `setText()`, `setTextColor()`, `setTextSize()`, `getText()`, `getTextSize()`, `getTextColors()` - methods works by following their name
- `setOnClickListener()`- sets a listener to be invoked when the TextView is clicked.
- `setTypeface()` - 
- `editText.

# Activity
Activity is a single screen with UI
<pre>
                onCreate -> onStart -> onResume 
                         <b>OTHER ACTIVITY</b> 
                        onPause -> onStop
                            <b>REOPEN</b> 
               onRestart -> onStart -> onResume
                    <b>CLOSE APP, BACK BUTTON</b>
                onPause -> onStop -> onDestroy
</pre>
Let's see the 7 lifecycle methods of android activity.
<img src="https://static.javatpoint.com/images/androidimages/Android-Activity-Lifecycle.png">

### Navigate Activity
Intent class is used to navigate through activity. Intent class accept two parameter, first one is current activity, and another one is navigated activity.
```
Intent intent = new Intent(this, SecondActivity.class);
startActivity(intent);
```

### Pass Data Between Activity
__Send__

`intent.putExtra()` - is used to send extra data with key value pair
```
intent.putExtra("EXTRA_MESSAGE", "Hello from MainActivity!");
```
__Recieve__

`getIntent()` and `getStringExtra()` - is used to retreive data from activity
```
Intent intent = getIntent();
String message = intent.getStringExtra("EXTRA_MESSAGE");
```
```
Bundle bundle = getIntent().getStringExtra("EXTRA_MESSAGE");
if(bundle!=null){
    String value=bundle.getString("EXTRA_MESSAGE");
    textView.setText(value);
}
```