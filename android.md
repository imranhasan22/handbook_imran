# XML - eXtensible Markup Language
It is a versatile markup language primarily designed to store and transport data.
- XML files often start with a prolog defining the XML version and encoding.(__< ?xml version="1.0" encoding="UTF-8"? >__)
- It allows users to define their own customized tags, similar to HTML, but not need to be predefined.
- XML documents are structured hierarchically. There is one root element, and all other elements are nested within it.
- It is `case-sensitive`

XML used in android development primarily for defining the user interface (UI) layouts and resource files.

`xmlns`(XML Namespace) is a mechanism in XML to avoid element name conflicts by qualifying names that may have the same name but different meanings or contexts.

# Index
- Layout
    - [LinearyLayout](https://github.com/masum184e/programming_notes/blob/main/android.md#linearlayout)
    - [RelativeLayout](https://github.com/masum184e/programming_notes/blob/main/android.md#relativelayout)
    - [ConstraintLayout](https://github.com/masum184e/programming_notes/blob/main/android.md#constraintlayout)
    - [GridLayout](https://github.com/masum184e/programming_notes/blob/main/android.md#gridlayout)
    - [AbsoluteLayout](https://github.com/masum184e/programming_notes/blob/main/android.md#absolutelayout)
- ViewGroup
    - [ListView](https://github.com/masum184e/programming_notes/blob/main/android.md#listview)
    - [ScrollView](https://github.com/masum184e/programming_notes/blob/main/android.md#scrollview)
- Views
    - [ZoomControls](https://github.com/masum184e/programming_notes/blob/main/android.md#zoomcontrols)
    - [CalendarView](https://github.com/masum184e/programming_notes/blob/main/android.md#calendarview)
    - [AnalogClock](https://github.com/masum184e/programming_notes/blob/main/android.md#analogclock)
    - [TextClock](https://github.com/masum184e/programming_notes/blob/main/android.md#textclock)
    - [TextView](https://github.com/masum184e/programming_notes/blob/main/android.md#textview)
    - [ImageView](https://github.com/masum184e/programming_notes/blob/main/android.md#imageview)
    - [RatingBar](https://github.com/masum184e/programming_notes/blob/main/android.md#ratingbar)
    - [SeekBar](https://github.com/masum184e/programming_notes/blob/main/android.md#seekbar)
    - [ProgressBar](https://github.com/masum184e/programming_notes/blob/main/android.md#progressbar)
    - [Switch](https://github.com/masum184e/programming_notes/blob/main/android.md#switch)
    - [DatePicker](https://github.com/masum184e/programming_notes/blob/main/android.md#datepicker)
    - [TimePicker](https://github.com/masum184e/programming_notes/blob/main/android.md#timepicker)
    - [NumberPicker](https://github.com/masum184e/programming_notes/blob/main/android.md#numberpicker)
- [Themes](https://github.com/masum184e/programming_notes/blob/main/android.md#themes)
- [Styling](https://github.com/masum184e/programming_notes/blob/main/android.md#styling)
- [Eventlistener](https://github.com/masum184e/programming_notes/blob/main/android.md#eventlistener)
- [Database](https://github.com/masum184e/programming_notes/blob/main/android.md#database)
# Layouts
## LinearLayout
It arranges its child views in a single direction, either vertically or horizontally. This makes it a straightforward choice for creating simple layouts where views are stacked in a single column or row.

- `android:orientation` - determine the direction of the child view
    - `vertical` - stack children from top to bottom
    - `horizontal` - places children side by side from left to right
- `android:gravity` - Aligns the content of a view within its own boundaries.(use in parent)
- `android:layout_gravity` - Aligns the view itself within its parent's boundaries.(use in child)
- `android:layout_weight` -  distribute space among child views. It allows you to specify how much of the extra space in the layout should be allocated to each child view. This attribute only works when the size of the view is set to `0dp`
- `android:weightSum` - defines the total weight of all child views.

LinearLayout is easy to understand and implement. It provides a predictable way to arrange views in a single direction. Allows for easy alignment of child views along a single axis. But LinearLayout lead to poor performance, as the layout becomes more complex and takes longer to render.
## RelativeLayout
It allows you to position and size child views in relation to each other or to the parent container.

- `android:layout_alignParentTop`, `android:layout_alignParentBottom`, `android:layout_alignParentLeft`, `android:layout_alignParentRight` - Aligns the child view to the corresponding edge of the __parent__.
- `android:layout_centerInParent`, `android:layout_centerHorizontal`, `android:layout_centerVertical` - Centers the child view in the __parent__, either completely or along one axis.
- `android:layout_above`, `android:layout_below`, `android:layout_toLeftOf`, `android:layout_toRightOf` - Positions the child view relative to __another child view__.
- `android:layout_margin`, `android:layout_marginTop`, `android:layout_marginBottom`, `android:layout_marginLeft`, `android:layout_marginRight` - Sets the space around the child view.
- `android:layout_alignTop`, `android:layout_alignBottom`, `android:layout_alignLeft`, `android:layout_alignRight` - Aligns the edges of __two child views__.

It allows for complex layouts where child views can be positioned relative to each other and to the parent. It helps to avoid deeply nested layouts, which can improve performance and useful for responsive designs where the position of views may change based on different screen sizes or orientations.
## ConstraintLayout
It allows you to position and size widgets in a flexible way without nesting multiple layouts. Widgets can be constrained to each other or the parent layout. This allows for precise control over the positioning. It reduce the hierchy of view group.

- `app:layout_constraintEnd_toEndOf` - make the view constraint from right
- `app:layout_constraintBottom_toBottomOf` - make the view constraint from bottom
- `app:layout_constraintStart_toStartOf` - make the view constraint from left
- `app:layout_constraintTop_toTopOf` - make the view constraint from top
- `tools:layout_editor_absoluteX`, `layout_editor_absoluteY` are ignorable, it has no effect in run time.
- `Inferror Constraints` button set the view where it is in the layout.
- Must constraint the view horizontally & vertically
- __Chain__ property work like two way constraint
- __Guideline__ property work like margin
- View doesn't have `match_parent` property, it use `match_constraint` or `0dp` for similar task

[Explore More](https://www.geeksforgeeks.org/constraintlayout-in-android/)

## GridLayout
__Parent Attributes:__
- `android:rowCount`: Specifies the total number of rows in the grid.
- `android:columnCount`: Specifies the total number of columns in the grid.

__Child Attributes:__
- `layout_row`: Defines the row index of a child.
- `layout_column`: Defines the column index of a child.
- `layout_rowSpan`: Specifies how many rows the child should span.
- `layout_columnSpan`: Specifies how many columns the child should span.

It's depricated, use __flow__ property of __constraint layout__.
## AbsoluteLayout
It allow to specify the exact x and y coordinates for each view within the layout. Each child view is positioned based on its x and y coordinates.
```
<AbsoluteLayout>
    <Button android:layout_x="50dp" android:layout_y="50dp"/>
</AbsoluteLayout>
```
Absolute Layout is __deprecated__.
# ViewGroup
## ListView
Each item in the list is an instance of View, which by default is a TextView but can be any layout.
### ArrayAdapter
The Adapter acts as a bridge between the UI Component and the Data Source. It converts data from the data sources into view items that can be displayed into the UI Component. Data Source can be Arrays, HashMap, Database, etc. and UI Components can be ListView, GridView, Spinner, etc. When you have a list of single type items which are stored in an array you can use ArrayAdapter.

ArrayAdapter has a layout with a single TextView. If you want to have a more complex layout instead of ArrayAdapter use [CustomArrayAdapter](https://www.geeksforgeeks.org/custom-arrayadapter-with-listview-in-android/). 
```
private ListView listView = findViewById(R.id.listView);
String[] items = {"Item 1", "Item 2", "Item 3", "Item 4", "Item 5"};
ArrayAdapter<String> adapter = new ArrayAdapter<>(this, android.R.layout.simple_list_item_1, items);
listView.setAdapter(adapter);
listView.setOnItemClickListener(new AdapterView.OnItemClickListener() {
       @Override
       public void onItemClick(AdapterView<?> parent, View view, int position, long id) {
           String selectedItem = (String) parent.getItemAtPosition(position);
           Toast.makeText(MainActivity.this, "Clicked: " + selectedItem, Toast.LENGTH_SHORT).show();
       }
   });
```
The `simple_list_item_1` layout is defined in the Android SDK. You don't need to create or modify it. You can directly use it in your adapters. It consists of a single TextView element that is used to display the text of each item in the list. It's the layout for list item, you can use your own layout also.
## ScrollView
A view group that allows the view hierarchy placed within it to be scrolled vertically. 
## HorizontalScrollView 
A view group that allows the view hierarchy placed within it to be scrolled horizontally.

It  can only contain a `single` child view or a single layout. Avoid nesting ScrollView with other scrollable views, as it can lead to performance issues and an unpredictable user experience.
```
scrollView.setLayoutParams(new ScrollView.LayoutParams(ScrollView.LayoutParams.MATCH_PARENT, ScrollView.LayoutParams.MATCH_PARENT));
LinearLayout linearLayout = new LinearLayout(this);
linearLayout.setLayoutParams(new LinearLayout.LayoutParams(LinearLayout.LayoutParams.MATCH_PARENT, LinearLayout.LayoutParams.WRAP_CONTENT));
linearLayout.setOrientation(LinearLayout.VERTICAL);

for (int i = 1; i <= 20; i++) {
    TextView textView = new TextView(this);
    textView.setLayoutParams(new LinearLayout.LayoutParams(LinearLayout.LayoutParams.MATCH_PARENT, LinearLayout.LayoutParams.WRAP_CONTENT));
    textView.setText("Item " + i);
    linearLayout.addView(textView);
}
scrollView.addView(linearLayout);
setContentView(scrollView);
```
__Attributes:__
- `android:fillViewport`: If set to true, the ScrollView will stretch its content to fill the viewport.
- `android:scrollbars`: Allows you to specify the visibility and style of scrollbars (e.g., none, vertical, horizontal).
__Methods:__
- `scrollTo(int x, int y)`: Scroll to the specified position.
- `smoothScrollTo(int x, int y)`: Smoothly scroll to the specified position.
- `fullScroll(int direction)`: Scroll to the beginning or end of the scroll view.

__Smooth Scrolling:__
```
goBottomButton.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) {
        scrollView.post(new Runnable() {
            @Override
            public void run() {
                scrollView.smoothScrollTo(0, scrollView.getBottom());
                //  scrollView.smoothScrollTo(0, 500); // Smooth scroll to 500 pixels down
                //  horizontalScrollView.smoothScrollTo(horizontalScrollView.getChildAt(0).getWidth(), 0);
            }
        });
    }
});
```
# Views
## ZoomControls
```
//  <ZoomControls android:id="@+id/zoomControls" />
private ZoomControls zoomControls = findViewById(R.id.zoomControls);
zoomControls.getChildAt(0).setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) {
        Toast.makeText(MainActivity.this, "Zoom Out", Toast.LENGTH_LONG).show();
    }
});
zoomControls.getChildAt(1).setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) {
        Toast.makeText(MainActivity.this, "Zoom In", Toast.LENGTH_LONG).show();
    }
});
```
## CalendarView
__Attributes:__
- `android:firstDayOfWeek`: Sets the first day of the week.
- `android:minDate`: Limits the selectable dates to those on or after the specified date.
- `android:maxDate`:  Limits the selectable dates to those on or before the specified date.
- `android:showWeekNumber`: Shows or hides the week numbers.


__Handling Date Selection:__
```
CalendarView calendarView = findViewById(R.id.calendarView);
calendarView.setOnDateChangeListener(new CalendarView.OnDateChangeListener() {
    @Override
    public void onSelectedDayChange(CalendarView view, int year, int month, int dayOfMonth) {
        String date = dayOfMonth + "/" + (month + 1) + "/" + year;
        Toast.makeText(MainActivity.this, "Selected date: " + date, Toast.LENGTH_SHORT).show();
    }
});
```
To change the color of selector, use theme attribute and to make more grip on calendar related task explore material design.
## AnalogClock
It shows the current time using hour, minute, and second hands.
```
<AnalogClock android:id="@+id/analogClock" />
```
## TextClock
It shows the current time in a digital format.

__Attributes:__
- `android:format12Hour`: Specifies the format string for 12-hour mode(hh:mm:ss a).
- `android:format24Hour`: Specifies the format string for 24-hour mode(HH:mm:ss).
- `android:timeZone` - Set time zone

__XML Layout:__
```
<TextClock android:id="@+id/textClock" />
```
## WebView
- `loadUrl()` - Loads the given URL
- `webView.setWebViewClient(new WebViewClient())` - Sets a WebViewClient to handle various web events. Enable navigating multiple webpage within the application.
- `WebSettings` - Configure various settings for the WebView.
```
WebSettings webSettings = webView.getSettings();
webSettings.setJavaScriptEnabled(true); // Enable JavaScript
webSettings.setCacheMode(WebSettings.LOAD_NO_CACHE); // Disable caching
webSettings.setDomStorageEnabled(true); // Enable DOM storage
```
__Handling Back Button:__

Handle back button so that it doesn't close the entire application
```
OnBackPressedDispatcher onBackPressedDispatcher =getOnBackPressedDispatcher();
onBackPressedDispatcher.addCallback(this, new OnBackPressedCallback(true) {
    @Override
    public void handleOnBackPressed() {
        if (webView.canGoBack()) {
            webView.goBack();
        } else {
            finish();
        }
    }
});
```
### HTML Content
__WebView:__
```
String htmlContent = "<html><body><h1>Hello, World!</h1><p>This is a sample HTML content.</p></body></html>";
webView.loadData(htmlContent, "text/html", "UTF-8");
// webView.loadUrl("file:///android_asset/index.html"); // Local file
```
__TextView:__
```
String htmlContent = "<h1>Hello, World!</h1><p>This is <b>bold</b> and <i>italic</i> text.</p>";
CharSequence styledText = Html.fromHtml(htmlContent);
textView.setText(styledText);
textView.setMovementMethod(LinkMovementMethod.getInstance()); // Handle clicks on links
```
## TextView
- `android:text` - sets the initial text displayed by the View
- `android:layout_width` or `android:layout_height` - sets the widht and height of the view. Possible values are:
    - `match_parent` - it will set the entire height/width of parent view 
    - `wrap_content`- it will set the space as much as needed
- `android:id` - assigned identifier is used to refer the view in java/kotlin
- `android:textColor` - sets the color of the text.
- `android:textSize` - sets the font size of the text.
- `android:visibility` - control the visibility. Possible values are `visible`, `invisible`, `gone`.
- `android:backgroundTint` - specify a color overlay to the background of drawable item.
## ImageView
- `android:src` - specify the image to be displayed
- `android:scaleType` - control how an image is resized. Possible values are:
    - `fitXY` - scale the image to fit exactly within the view
    - `fitStart` - scale the image to fit within the view and align it to the top left.
    - `fitEnd` - scale the image to fit within the view and align it to the bottom right.
    - `fitCenter` - scale the image to fit within the view and center it.
- `android:adjustViewBounds` - adjust the bounds to maintain the aspect ratio. Possible values are true or false.

Always try to use `png` images while working with android studio.
## RatingBar
- `android:numStars`: Sets the number of stars in the RatingBar.
- `android:rating`: Sets the initial rating of the RatingBar.
- `android:stepSize`: Sets the step size of the rating. For example, if the step size is 0.5, the rating can be 0.5, 1.0, 1.5, etc.
- `android:isIndicator`: If set to true, the RatingBar is in indicator mode and the user cannot change the rating.
- `android:progressDrawable`: Sets a drawable(design) to be used for the progress indicator.

__Interact with Java:__
```
ratingBar.setOnRatingBarChangeListener(new RatingBar.OnRatingBarChangeListener() {
    @Override
    public void onRatingChanged(RatingBar ratingBar, float rating, boolean fromUser) {
        Toast.makeText(getApplicationContext(), "Rating: " + rating, Toast.LENGTH_SHORT).show();
    }
});
```

## SeekBar
It's as same as input type range in HTML
- `android:max`: Sets the maximum value of the SeekBar.
- `android:progress`: Sets the initial progress value of the SeekBar.
- `android:thumb`: Sets a drawable for the thumb.
- `android:progressDrawable`: Sets a drawable for the progress line.

__Interact with Java:__
```
seekBar.setOnSeekBarChangeListener(new SeekBar.OnSeekBarChangeListener() {
    @Override
    public void onProgressChanged(SeekBar seekBar, int progress, boolean fromUser) {
        // Handle progress change
        Toast.makeText(getApplicationContext(), "Progress: " + progress, Toast.LENGTH_LONG).show();
    }

    @Override
    public void onStartTrackingTouch(SeekBar seekBar) {
        // Handle start of tracking touch
        Toast.makeText(MainActivity.this, "Start Track Touched", Toast.LENGTH_LONG).show();
    }

    @Override
    public void onStopTrackingTouch(SeekBar seekBar) {
        // Handle stop of tracking touch
        Toast.makeText(MainActivity.this, "Stop Track Touched", Toast.LENGTH_LONG).show();
    }
});
```

- `onProgressChanged` - handle the change of the progress
- `onStartTrackingTouch` - handle the tracking touch of the progress
- `onStopTrackingTouch` - handle the stop tracking touch of the progress

## ProgressBar
-  `android:max`: Sets the maximum value of the determinate ProgressBar.
-  `android:progress`: Sets the initial progress value of the determinate ProgressBar.
-  `android:indeterminate`: If set to true, the ProgressBar is indeterminate.
-  `android:progressDrawable`: Sets a drawable for the progress indicator.
-  `android:indeterminateDrawable`: Sets a drawable for the indeterminate progress indicator.

__Interact with Java:__
- `getProgress()`, `setProgress()` - perform task following their name 

## Switch
It is a subclass of `CompoundButton`
- `android:text`: Sets the text label for the Switch.
- `android:checked`: Sets the initial checked state of the Switch.
- `android:thumb`: Sets a drawable for the thumb (the part that moves).
- `android:track`: Sets a drawable for the track (the part that stays fixed).
- `android:switchTextAppearance`: Sets the text appearance for the Switch.
- `android:switchMinWidth`: Sets the minimum width of the Switch(without text).
- `android:switchPadding`: Sets the padding between the switch and the text.
- `android:showText`: Sets whether to show text (On/Off) inside the switch.

__Interact with Java:__
```
switch1.setOnCheckedChangeListener((buttonView, isChecked) -> {
    if (isChecked) {
        // Switch is on
        Toast.makeText(getApplicationContext(), "Switch is ON", Toast.LENGTH_LONG).show();
    } else {
        // Switch is off
        Toast.makeText(getApplicationContext(), "Switch is OFF", Toast.LENGTH_LONG).show();
    }
});
```
## EditText
It is a subclass of `TextView` 
- `android:inputType` - specify the type of the data. Possible values are:
- `android:textCapWords` - Capitalize the first letter of each word.
- `android:textCapCharacters` - Capitalize all characters.
- `android:textCapSentences` - Capitalize the first letter of each sentence.
- `android:textAutoCorrect` - Enable auto-correction.
- `android:textMultiLine` - Allow multiple lines of text input.
- `android:hint` - set placeholder
- `android:text` - set the initial text
- `android:maxLength` - specify the maximum length of the text can be entered
- `android:imeOptions` - specify additional options for an input method editor. This will display a `Go`, `Search`, `Enter`, `Done` button on the keyboard. Possible values are `actionDone`, `actionGo`, `actionNext`, `actionSearch`, `actionSend`, `flagNoFullscreen`
- `android:textCursorDrawble` - customize the appearance of the cursor. You need to create a custom drawable resource and apply it here.
- `clearFocus()` - dismiss the soft keyboard if it's open
- `getText()`, `setText()` - perform task following their name 

__Interact with Java:__
```
editText.addTextChangedListener(new TextWatcher() {
    @Override
    public void beforeTextChanged(CharSequence s, int start, int count, int after) {
        // Do something before text is changed
    }

    @Override
    public void onTextChanged(CharSequence s, int start, int before, int count) {
        // Do something as the text is being changed
    }

    @Override
    public void afterTextChanged(Editable s) {
        // Do something after the text has changed
    }
});
```
## DatePicker
- `android:minDate` - The earliest selectable date.
- `android:maxDate` - The latest selectable date.

__Interact with Java:__
```
datePicker.setOnDateChangedListener(new DatePicker.OnDateChangedListener() {
    @Override
    public void onDateChanged(DatePicker datePicker, int year, int month, int date) {
        Toast.makeText(MainActivity.this, year+" "+month+" "+date, Toast.LENGTH_LONG).show();
    }
});
```
## TimePicker
- `android:timePickerMode` - Specifies whether the time picker should use a spinner or a clock-style interface.
    - `spinner` - shows hours and minutes in a dropdown-style spinner.
    - `clock` - provides a clock-style interface for selection.
- `setIs24HourView(true)` - make the time in a 24-hour format.

__Interact with Java:__
```
timePicker.setOnTimeChangedListener(new TimePicker.OnTimeChangedListener() {
    @Override
    public void onTimeChanged(TimePicker view, int hourOfDay, int minute) {
        Calendar calendar = Calendar.getInstance();
        calendar.set(Calendar.HOUR_OF_DAY, hourOfDay);
        calendar.set(Calendar.MINUTE, minute);

        // Format the time to 12-hour format with AM/PM
        SimpleDateFormat sdf = new SimpleDateFormat("hh:mm a", Locale.getDefault());
        String time = sdf.format(calendar.getTime());

        // Show the time in a Toast message
        Toast.makeText(MainActivity.this, "Selected time: " + time, Toast.LENGTH_LONG).show();
    }
});
```
## NumberPicker
It allow users to select a number from a predefined range.
- `setMinValue` - Minimum value displayed in the NumberPicker.
- `setMaxValue` - Maximum value displayed in the NumberPicker.
- `setValue` - Initial value displayed in the NumberPicker.
- `setWrapSelectorWheel` - Whether to wrap the selector wheel when reaching the minimum or maximum value.
- `setDisplayedValues` - Sets list of values displayed in the NumberPicker.

__Interact with Java:__
```
numberPicker.setOnValueChangedListener(new NumberPicker.OnValueChangeListener() {
    @Override
    public void onValueChange(NumberPicker picker, int oldVal, int newVal) {
        // Handle value change
        selectedValueTextView.setText("Selected Value: " + newVal+" "+oldVal);
    }
});
```

# Themes
- Theme.Holo
- Theme.Holo.Light
- Theme.Material
- Theme.Material.Light
- Theme.AppCompat
- Theme.AppCompat.Light
- Theme.AppCompat.Light.DarkActionBar
- Theme.AppCompat.DayNight
- Theme.AppCompat.DayNight.DarkActionBar
- Theme.AppCompat.NoActionBar
- Theme.AppCompat.Light.NoActionBar
- Theme.AppCompat.DayNight.NoActionBar
# Styling
Themes are applied to entire activities or applications, while styles are applied to individual views. 

__Define a Style:__
```
<resources>
    <style name="styleName" parent="parentName">
        <item name="viewAttribute">attributeValue</item>
    </style>
</resources>
```
__Explore:__
    - style theme
    - style activity
    - style view
    
Set the style to an activity with `android.theme` attribute

__Inherit Style:__
```
<resources>
    <style name="styleName" parent="parentStyleName">
        <item name="viewAttribute">attributeValue</item>
    </style>
</resources>
```
## Shape
- `<solid>` tag specifies the fill color of the shape.
- `<stroke>` tag defines the border width and color.
- `<corners>` tag allows you to set the radius for rounded corners.
- `<padding>` tag specifies the padding inside the shape.
- `<size>` tag can define the width and height of the shape (useful for lines and rings).
- `<shape>` is the container tag, shape type is set by `android:shape` attribute along with shape tag

__Rectangle:__
```
<shape xmlns:android="http://schemas.android.com/apk/res/android">
    <solid android:color="#e9ecf3" />
    <corners android:radius="8dp" />
    <stroke android:width="2dp" android:color="#c0c0c0" />
    <padding android:left="10dp" android:top="10dp" android:right="10dp" android:bottom="10dp" />
</shape>
```
# Eventlistener
- `Button myButton = findViewById(R.id.myButton)` - finds a button with the id `myButton` defined in the layout XML file and assigns it to a variable named myButton.

    It should be declare outside of `onCreate` and initialize inside it.
- `myButton.setOnClickListener(new View.OnClickListener() { ... })` - sets an OnClickListener on the button called `myButton`.

## Handling Multiple Eventlistner

- __Implement the Listener Interfaces:__ Implement the listener interfaces for the events you want to handle. For example, if you want to handle click events on buttons, you'll implement the View.OnClickListener interface.
```
public class MainActivity extends AppCompatActivity implements View.OnClickListener {
    ...
}
```
- __Register the Listeners:__ Register the listener instances with the appropriate views.
```
Button myButton = findViewById(R.id.myButton);
myButton.setOnClickListener(this);
```

- __Override the Listener Methods:__ Implement the required methods of the listener interfaces which will contain the logic that you want to execute when the corresponding events occur.
```
@Override
public void onClick(View view) {
    ...
}
```
__Boilerplate:__
```
public class MainActivity extends AppCompatActivity implements View.OnClickListener {

  @Override
  protected void onCreate(Bundle savedInstanceState) {
    Button myButton = findViewById(R.id.myButton);
    myButton.setOnClickListener(this);
  }

  @Override
  public void onClick(View view) {
    if(v.getId()==R.id.myButton){
      myText.setText("Button is clicked");
    }
  }
}
```
## Inner Class
- __Instantiate the Inner Class and Set the Listener:__ Instantiate an object of the inner class and set it as the listener for the view using the `setOnClickListener` method.
```
myButton.setOnClickListener(new MyButtonClickListener());
```
- __Define the Inner Class:__ Define an inner class within your activity class. It will implement the interface corresponding to the event you want to handle. In this case, we're handling click events, so the inner class implements View.OnClickListener.
```
private class MyButtonClickListener implements View.OnClickListener {
    @Override
    public void onClick(View view) {
        ...
    }
}

```

__Boilerplate:__
```
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        ...
        myButton.setOnClickListener(new MyButtonClickListener());
    }

    private class MyButtonClickListener implements View.OnClickListener {
        @Override
        public void onClick(View view) {
            if(v.getId()==R.id.myButton){
                myText.setText("Button is clicked");
            }
        }
    }
}
```
## Event Handler in XML
__XML:__
```
<Button ... android:onClick="onButtonClick" />
```
__JAVA:__
```
public void onButtonClick(View view) {
  Toast.makeText(this, "Button clicked", Toast.LENGTH_SHORT).show();
}
```
## View Methods
- `setText()`, `setTextColor()`, `setTextSize()`, `getText()`, `getTextSize()`, `getCurrentTextColor()` - methods works by following their name
- `setOnClickListener()`- sets a listener to be invoked when the TextView is clicked.
- `setTypeface()` - set the font
- `getId()` - gets the view ID
# Database
## SharedPreferences
It is used for storing small amounts of primitive data in key-value pairs. You can use it for storing user setting, last score, location caching

__Store Data:__
```
SharedPreferences.Editor editor = sharedPreferences.edit();
editor.putString("key", "value");
editor.putInt("key", 123);
editor.apply();  // or editor.commit();
```
__Retrieve Data:__
```
SharedPreferences sharedPreferences = getSharedPreferences("MyPreferences", Context.MODE_PRIVATE);
if(sharedPreferences.contains("key")){
  String value = sharedPreferences.getString("key", "default_value");
  int number = sharedPreferences.getInt("key",123);
}
```
## Internal Storage - File
Use internal storage to store private data within the device's internal memory.

__Store Data:__
```
String filename = "myfile.txt";
String fileContents = "Hello World!";
FileOutputStream fos = openFileOutput(filename, Context.MODE_PRIVATE);
fos.write(fileContents.getBytes());
fos.close();
```
__Retrieve Data:__
```
String filename = "myfile.txt";
FileInputStream fis = openFileInput(filename);
InputStreamReader isr = new InputStreamReader(fis);
BufferedReader bufferedReader = new BufferedReader(isr);
StringBuilder sb = new StringBuilder();
String line;
while ((line = bufferedReader.readLine()) != null) {
    sb.append(line);
}
String fileContents = sb.toString();
```
# File Structure
```
app
├─ build
├─ libs
├─ src
│   ├─ main
│   │   ├─ java
│   │   │   └─ com/example/myapplication
│   │   │    
│   │   ├─ res
│   │   │   ├─ layout - store XML layout files that define the user interface of your activities and fragments.
│   │   │   │   
│   │   │   ├─ drawable - store drawable resources such as PNG files, vector graphics, and XML shapes.
│   │   │   │   
│   │   │   ├─ values - store XML files that define values like strings, colors, and dimensions. Common files include strings.xml, colors.xml, and dimens.xml.
│   │   │   │
│   │   │   ├─ mipmap - store resources for application icons, typically in different resolutions.
│   │   │   │   
│   │   │   └─ menu - store XML files that define menus for activities or fragments.
│   │   │   
│   │   │  
│   │   └─ manifests
│   │       └─ AndroidManifest.xml - It describes essential information about your app, including the package name, components (activities, services, broadcast receivers, content providers), permissions, and other application-level configurations.
│   ├─ androidTest
│   │   └─  java
│   │       └─ com/example/myapplication
│   │           └─ ExampleInstrumentedTest.java
│   └─ test
│      └─ java
│          └─ com/example/myapplication
│             
└─ build.gradle

```

### TableLayout
A type of `ViewGroup` that arranges it's child in grid format.  It organizes views into rows and columns, and allows for complex layouts where alignment and spacing are important.

It consists of `TableRow` objects, each representing a row in the table.
- `android:stretchColumns`
- `android:shrinkColumns`
- `android:collapseColumns`
- `android:layout_span`
- `android:layout_column`

### FrameLayout
It is designed to block out an area on the screen to display a single item. Generally, It is used to hold a single child view, but it can also be used to overlay multiple child views, stacking them on top of each other. It display view layer by layer and one layer at a time.
- `android:foreground` 
- `android:foregroundGravity`
- `android:measureAllChildren`

# View

### Alert
```
        AlertDialog.Builder builder = new AlertDialog.Builder(MainActivity.this);
        builder.setTitle("Alert Dialog Title")
                .setMessage("This is the message of the alert dialog.")
                .setIcon(android.R.drawable.ic_dialog_alert)
                .setPositiveButton("OK", new DialogInterface.OnClickListener() {
                    public void onClick(DialogInterface dialog, int which) {
                        // Action for 'OK' Button
                    }
                })
                .setNegativeButton("Cancel", new DialogInterface.OnClickListener() {
                    public void onClick(DialogInterface dialog, int which) {
                        // Action for 'Cancel' Button
                    }
                })
                .setNeutralButton("Later", new DialogInterface.OnClickListener() {
                    public void onClick(DialogInterface dialog, int which) {
                        // Action for 'Later' Button
                    }
                });

        // Show the AlertDialog
        AlertDialog alert = builder.create();
        alert.show();
```

- `setcancelable=false` - used to prevent a dialog from being dismissed when the user touches outside of the dialog.

### Toast
```
Toast.makeText(MainActivity.this, "Hello Toast", Toast.LENGTH_SHORT).show();
```

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
# Toast
### Custom Toast
1. __Custom Layout for Toast:__
```
<LinearLayout android:id="@+id/customToast">
    <ImageView android:id="@+id/toast_icon" />
    <TextView android:id="@+id/toast_message" />
</LinearLayout>
```
2. __Inflate the custom layout for the Toast:__
```
LayoutInflater inflater = getLayoutInflater();
View layout = inflater.inflate(R.layout.custom_toast,(ViewGroup)findViewById(R.id.custom_toast_id));
```
3. __Create and show the Toast:__
```
Toast customToast = new Toast(MainActivity.this);
customToast.setDuration(Toast.LENGTH_LONG);
customToast.setGravity(Gravity.CENTER, 0, 0);
customToast.setView(layout);
customToast.show();
```

# Logging
It allow developers to track the flow of their application, debug issues, and monitor behavior during runtime. Android provides a built-in logging framework through the `android.util.Log` class, which allows developers to output log messages of varying severity levels.

### Log Levels
1. __Verbose:__ The least important level, typically used for providing detailed information during debugging.
2. __Debug:__ Used for debugging messages. These messages are useful during development but should be disabled in production builds.
3. __Info:__ Used for informational messages that highlight the progress of the application. These messages can be useful for tracking significant application events.
4. __Warning:__ Used to indicate potential issues that do not prevent the application from functioning but should be addressed.

5. __Error:__ Used to log error conditions that might cause the application to crash or behave unexpectedly.

6. __Assert:__ Used to log assertions, indicating conditions that should never occur. This level is typically used for critical errors.

### Logging Methods

`Log.v()`,`Log.d()`,`Log.i()`,`Log.w()`,`Log.e()`,`Log.wtf()` is used for verbose, debug, informational,  warning, error, assertion message respectively. Each method required a tag and log message.

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

### Navigation
1. Declare Activities in `AndroidManifest.xml`:
```
<application ... >
    <activity android:name=".MainActivity">...</activity>
    <activity android:name=".SecondActivity" />
</application>
```
2. Handle `MainActivity`:

__XML File:__
```
<EditText android:id="@+id/inputBox" .../>
<Button android:id="@+id/myButton" onClick="handleNext" .../>
<TextView android:id="@+id/myView" .../>
```
__Java File:__
```
public class MainActivity extends AppCompatActivity {
    ...
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        ...
        myButton=findViewById(R.id.myButton);
        inputBox=findViewById(R.id.inputBox);
        myView=findViewById(R.id.myView);

        Intent intent = getIntent();
        String message = intent.getStringExtra("ACTIVITY_MESSAGE");
        if(message!=null){
            myView.setText("From Second Activity: "+message);
        }

    }

    public void handleNext(View v){
        if(v.getId()==R.id.myButton){
            Intent intent = new Intent(this, SecondActivity.class);
            intent.putExtra("ACTIVITY_MESSAGE", inputBox.getText().toString());
            startActivity(intent);
        }
    }
}
```
3. Handle `SecondActivity`:

__XML File:__
```
<EditText android:id="@+id/inputSecondBox" .../>
<Button android:id="@+id/mySecondButton" android:onClick="handlePrev" .../>
<TextView android:id="@+id/mySecondView" .../>
```
__Java File:__
```
public class SecondActivity extends AppCompatActivity {
    ...
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        ...
        mySecondView=findViewById(R.id.mySecondView);
        inputSecondBox=findViewById(R.id.inputSecondBox);
        mySecondButton=findViewById(R.id.mySecondButton);

        Intent intent = getIntent();
        String message = intent.getStringExtra("ACTIVITY_MESSAGE");
        if(message!=null){
            mySecondView.setText("From Main Activity: "+message);
        }

    }

    public void handlePrev(View v){
        if(v.getId()==R.id.mySecondButton){
            Intent intent = new Intent(this, MainActivity.class);
            intent.putExtra("ACTIVITY_MESSAGE", inputSecondBox.getText().toString());
            startActivity(intent);
        }
    }
}
```

`onCreate`, `onStart`, `onResume`, `onPause`, `onStop`, `onRestart`, `onDestroy` all are the instances of activity class. As you use onCreate method for initial rendering.

# AndroidManifest.xml
## Tags
- `<manifest>` - root element. It contains information about the application package and its components, as well as any permissions the application needs. Attributes are `package`, `versionCode`, `versionName`.
- `<application>` - container for application components such as activities, services, broadcast receivers, and content providers. It also contains various settings, such as application-level resources and metadata.
- `<activity>` - declares an activity, which is a single screen in an application. Each activity must be declared in the manifest file with certain attributes that define its behavior.
- `<intent-filter>` - used within `<activity>`, `<service>`, and `<receiver>` to specify the types of intents that the component can respond to. It contains one or more `<action>`, `<category>`, and `<data>` elements.
    - `<action>`: Declares the action an intent filter can handle.
        - `android.intent.action.MAIN`: The main entry point for an application. Typically used with the launcher activity.
        - `android.intent.action.VIEW`: Display data to the user.
        - `android.intent.action.EDIT`: Allow the user to edit data.
        - `android.intent.action.SEND`: Send data to another activity.
        - `android.intent.action.PICK`: Select an item from a list of items.
        - `android.intent.action.DELETE`: Delete data.
    - `<category>`: Declares the category an intent filter can handle.
        - `android.intent.category.DEFAULT`: The default category for activities. Should be included in all intent filters that are meant to respond to implicit intents.
        - `android.intent.category.LAUNCHER`: Indicates that the activity can be the initial activity of a task and should be displayed in the application launcher.
        - `android.intent.category.BROWSABLE`: Allows an activity to be started by a web browser to display data referenced by a link.
        - `android.intent.category.ALTERNATIVE`: Provides an alternative action for the user to choose.
        - `android.intent.category.SELECTED_ALTERNATIVE`: An alternative action that the user has selected.
        - `android.intent.category.TAB`: Specifies that an activity can be used as a tab.
    - `<data>`: Declares the type of data an intent filter can handle.

## Attributes
- `android:icon` -  Specifies the default icon for the application
- `android:label` - Specifies the default label (name) for the application
- `android:roundIcon` - Specifies the round icon for devices that support round icons
- `android:supportsRtl` - Indicates whether the application supports right-to-left (RTL) layouts. 

# ActionBar
### Adding ActionBar
```
<application
    ...
    android:theme="@style/Theme.AppCompat.Light.DarkActionBar">
    <activity
        ...
        android:theme="@style/Theme.AppCompat.Light.DarkActionBar">
    </activity>
</application>
```
### Customize ActionBar
```<resources>
    <style name="AppTheme" parent="Theme.AppCompat.Light.DarkActionBar">
        <item name="colorPrimary">@color/colorPrimary</item>
    </style>
</resources>

```
### Accessing ActionBar
```
ActionBar actionBar = getSupportActionBar();
if (actionBar != null) {
    actionBar.setTitle("My Title");
    actionBar.setSubtitle("My Subtitle");
    actionBar.setDisplayHomeAsUpEnabled(true); // Show the Up button
    actionBar.setHomeButtonEnabled(true); // Enable the Home button
    actionBar.setLogo(R.drawable.logo); // Set the logo
    actionBar.setDisplayUseLogoEnabled(true); // Enable display of the logo
    actionBar.setDisplayShowTitleEnabled(false); // Optionally hide the title if you only want to show the logo
}

@Override
public boolean onOptionsItemSelected(MenuItem item) {
    switch (item.getItemId()) {
        case android.R.id.home:
            // Handle the back button click here
            onBackPressed();
            return true;
        default:
            return super.onOptionsItemSelected(item);
    }
}
@Override
public void onBackPressed() {
    // Handle the back press logic here, if needed
    super.onBackPressed();
}
```
Navigate back without `onOptionsItemSelected` through `android:parentActivityName` attribute in `activity` tag in `AndroidManifest.xml` 

### Adding Actions/Icons to ActionBar
```
<menu xmlns:android="http://schemas.android.com/apk/res/android">
    <item
        android:id="@+id/action_search"
        android:icon="@drawable/ic_search"
        android:title="Search"
        android:showAsAction="ifRoom" />
    <item
        android:id="@+id/action_settings"
        android:title="Settings"
        android:showAsAction="never" />
</menu>
```
### Inflate the menu in your activity
```
@Override
public boolean onCreateOptionsMenu(Menu menu) {
    getMenuInflater().inflate(R.menu.menu_main, menu);
    return true;
}
```