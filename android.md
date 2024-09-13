# XML - eXtensible Markup Language
It is a versatile markup language primarily designed to store and transport data.
- XML files often start with a prolog defining the XML version and encoding.(__< ?xml version="1.0" encoding="UTF-8"? >__)
- It allows users to define their own customized tags, similar to HTML, but not need to be predefined.
- XML documents are structured hierarchically. There is one root element, and all other elements are nested within it.
- It is `case-sensitive`

XML used in android development primarily for defining the user interface (UI) layouts and resource files.

`xmlns`(XML Namespace) is a mechanism in XML to avoid element name conflicts by qualifying names that may have the same name but different meanings or contexts.
# Android
## ADB vs AVD
__AVD(Android Virtual Device)__ refers to the emulator that allows you to simulate an Android device `on your computer`. It helps you test and run Android apps in a virtual environment `without` needing `a physical device`.

__ADB()__ is a command-line tool that allows developers to communicate with an Android device (`physical` or virtual) for debugging and performing various system-level tasks.

# Index
- Layout
    - [LinearyLayout](#linearlayout)
    - [RelativeLayout](#relativelayout)
    - [ConstraintLayout](#constraintlayout)
    - [GridLayout](#gridlayout)
    - [AbsoluteLayout](#absolutelayout)
    - [FrameLayout](#framelayout)
    - [TabLayout](#tablayout)
- ViewGroup
    - [ListView](#listview)
    - [ScrollView](#scrollview)
    - [CardView](#cardview)
- Views
    - [ZoomControls](#zoomcontrols)
    - [CalendarView](#calendarview)
    - [AnalogClock](#analogclock)
    - [TextClock](#textclock)
    - [TextView](#textview)
    - [ImageView](#imageview)
    - [RatingBar](#ratingbar)
    - [SeekBar](#seekbar)
    - [ProgressBar](#progressbar)
    - [Switch](#switch)
    - [Spinner](#spinner)
    - [DatePicker](#datepicker)
    - [TimePicker](#timepicker)
    - [NumberPicker](#numberpicker)
    - [RadioGroup](#radiogroup)
    - [ChipGroup](#chipgroup)
    - [AutoCompleteTextView](#autocompletetextView)
    - [View](#view)
- [Themes](#themes)
- [Styling](#styling)
- [Eventlistener](#eventlistener)
- [Inflater](#inflater)
- [Toast](#toast)
- [Activity](#activity)
- [Intent](#intent)
- [Fragment](#fragment)
- [Bottom Navigation](#bottom-navigation)
- [Actionbar](#actionbar)
- [Logging](#logging)
- [Database](#database)
- [Retrofit](#retrofit)
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

__Add Dependency:__
```
implementation("androidx.constraintlayout:constraintlayout:2.1.4")
```
Now sync your project.

__XML Layout:__
```
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent" android:layout_height="match_parent">
</androidx.constraintlayout.widget.ConstraintLayout>
```
__Constratint:__
- `app:layout_constraintEnd_toEndOf` - make the view constraint from right
- `app:layout_constraintBottom_toBottomOf` - make the view constraint from bottom
- `app:layout_constraintStart_toStartOf` - make the view constraint from left
- `app:layout_constraintTop_toTopOf` - make the view constraint from top

__Bias:__
A way to control the position of the view. The bias value ranges from 0(start) to 1(end).
- `app:layout_constraintHorizontal_bias` - control horizontal positioning.
- `app:layout_constraintVertical_bias` - control vertical positioning.
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
## FrameLayout
It is used to display a single child view. It is designed to hold a single child view by default, but if you add more than one child, they will be stacked on top of each other with the most recently added view appearing on top.

It used as the default layout of fragment container.

__Control the stack programmitically:__
```
layout.bringToFront();
```
## TabLayout
It provides a horizontal layout to display tabs. It often used in conjuction with `ViewPager` to navigate between different pages.

1. __Fragment__
Create fragment for each tab item.
2. __FragmentPagerAdapter__
```
public class TabAdapter extends FragmentPagerAdapter {
    private List<Fragment> fragmentList=new ArrayList<>();
    private List<String> fragmentTitleList=new ArrayList<>();
    public TabAdapter(@NonNull FragmentManager fm, int behavior) {
        super(fm, behavior);
    }

    @NonNull
    @Override
    public Fragment getItem(int position) {
        return fragmentList.get(position);
    }

    @Override
    public int getCount() {
        return fragmentList.size();
    }

    public void addFragment(Fragment fragment, String title){
        fragmentList.add(fragment);
        fragmentTitleList.add(title);
    }
    @Nullable
    @Override
    public CharSequence getPageTitle(int position) {
        return fragmentTitleList.get(position);
    }
}
```
3. __Merge__
```
ViewPager viewPager=findViewById(R.id.view_pager_container);
TabLayout tab_container=findViewById(R.id.tab_container);

TabAdapter tabAdapter=new TabAdapter(getSupportFragmentManager(), FragmentPagerAdapter.BEHAVIOR_RESUME_ONLY_CURRENT_FRAGMENT);
tabAdapter.addFragment(new FragA(), "BTN A");
tabAdapter.addFragment(new FragB(), "BTN B");

viewPager.setAdapter(tabAdapter);
tab_container.setupWithViewPager(viewPager);
```
## Layout
```
<com.google.android.material.tabs.TabLayout />
```
## ViewPager
It allow the user to swipe left or right through pages of content, typically fragments
```
<androidx.viewpager.widget.ViewPager  />
```
# ViewGroup
## ListView
Each item in the list is an instance of View, which by default is a TextView but can be any layout.
### ArrayAdapter
The Adapter acts as a bridge between the UI Component and the Data Source. It converts data from the data sources into view items that can be displayed into the UI Component. Data Source can be Arrays, HashMap, Database, etc. and UI Components can be ListView, GridView, Spinner, etc. When you have a list of single type items which are stored in an array you can use ArrayAdapter.

ArrayAdapter has a layout with a single TextView. If you want to have a more complex layout instead of ArrayAdapter use `CustomArrayAdapter/BaseAdapter`
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
### BaseAdapter
__Layout:__
```
<LinearLayout>
    <TextView android:id="@+id/title" />
    <TextView android:id="@+id/title" />
</LinearLayout>
```
__Model Class:__

`@models/Item`
```
public class Item {
    private String title;
    private String description;

    public Item(String title, String description) {
        this.title = title;
        this.description = description;
    }

    public String getTitle() {
        return title;
    }

    public String getDescription() {
        return description;
    }
}
```
__Custom Adapter:__

`@adapters/ItemAdapter`
```
public class ItemAdapter extends BaseAdapter {
    private Context context;
    private List<Item> items;

    public ItemAdapter(Context context, List<Item> items) {
        this.context = context;
        this.items = items;
    }

    @Override
    public int getCount() {
        return items.size();
    }

    @Override
    public Object getItem(int position) {
        return items.get(position);
    }

    @Override
    public long getItemId(int position) {
        return position;
    }

    @Override
    public View getView(int position, View view, ViewGroup parent) {
        if (view == null) {
            view = LayoutInflater.from(context).inflate(R.layout.list_item, parent, false);
            TextView title = view.findViewById(R.id.title);
            TextView description = view.findViewById(R.id.description);

            Item item = items.get(position);
            title.setText(item.getTitle());
            description.setText(item.getDescription());
        }
        return view;
    }
}
```
__Use Custom Adapter:__
```
List<Item> listItems = new ArrayList<>();
listItems.add(new Item("Title 1", "Description 1"));
listItems.add(new Item("Title 2", "Description 2"));
listItems.add(new Item("Title 3", "Description 3"));
listItems.add(new Item("Title 4", "Description 4"));

ItemAdapter itemAdapter=new ItemAdapter(this, listItems);
ListView listView = findViewById(R.id.listView);
listView.setAdapter(itemAdapter);
```
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
## CardView
It provides a layout that includes rounded corners and a shadow, making it look elevated above other content. 
__Add Dependency:__
```
implementation ("androidx.cardview:cardview:1.0.0")
```
__XML Layout:__
```
<androidx.cardview.widget.CardView xmlns:android="http://schemas.android.com/apk/res/android" xmlns:app="http://schemas.android.com/apk/res-auto" >
</androidx.cardview.widget.CardView>
```
- `app:cardCornerRadius`: To set the radius of the corners.
- `app:cardElevation`: To set the elevation (shadow) of the card.
- `app:cardBackgroundColor`: To set the background color of the card.
- `app:cardMaxElevation`: To set the maximum elevation.
- `app:cardUseCompatPadding`: To ensure that the content of the CardView doesn’t interfere with the card’s shadow.
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
## Spinner
Spinner is like ListView but it work like `select` tag in html. They both provide a dropdown menu that allows users to select one option from a list of choices.
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
## RadioGroup
Radio buttons are usually placed inside a RadioGroup to ensure that only one button can be selected at a time.
```
<RadioGroup
    android:id="@+id/radioGroup"
    >
    <RadioButton android:text="Male" />
    <RadioButton android:text="Female" />
    <RadioButton android:text="Other" />
</RadioGroup>
```
__Interact with Java:__
```
radioGroup.setOnCheckedChangeListener(new RadioGroup.OnCheckedChangeListener() {
    @Override
    public void onCheckedChanged(RadioGroup group, int checkedId) {
        RadioButton radioButton = findViewById(checkedId);
        Toast.makeText(getApplicationContext(), "Selected: " + radioButton.getText(), Toast.LENGTH_LONG).show();
    }
});
```
## ChipGroup
Chips are typically used to display tags, categories, or selections.

__Types of Chips:__

1. __Entry Chip:__ Used for inputting information.
2. __Filter Chip:__ Used for filtering content.
3. __Choice Chip:__ Used for single selection from a set.
4. __Action Chip:__ Used to trigger actions related to primary content.

__Add Dependency:__
```
implementation ("com.google.android.material:material:1.4.0")
```
Now sync your project.

__XML Layout:__
```
<com.google.android.material.chip.ChipGroup >
    <com.google.android.material.chip.Chip style="@style/Widget.MaterialComponents.Chip.Action" />
    <com.google.android.material.chip.Chip style="@style/Widget.MaterialComponents.Chip.Entry" />
    <com.google.android.material.chip.Chip style="@style/Widget.MaterialComponents.Chip.Filter" />
<com.google.android.material.chip.ChipGroup >
```
__ChipGroup Attributes:__
- `app:singleSelection` - only one chip can be selected at a time.
- `app:selectionRequired` - at least one chip must be selected.

__Chip Attributes:__
- `app:chipIcon` - set an icon on the chip.
- `app:chipBackgroundColor` - set the background color.
- `app:chipStrokeColor` - set the stroke color.
- `app:chipStrokeWidth` - set the stroke width.
- `app:closeIconEnabled` - enable a close icon on the chip.
- `app:closeIcon` - set a custom close icon.

__Interact with Java:__
```
chip_group=findViewById(R.id.chip_group);
btn=findViewById(R.id.btn);
btn.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View view) {
        Chip chip=new Chip(MainActivity.this);
        chip.setText("Chip 1");
        chip.setCloseIconVisible(true);

        chip.setOnCloseIconClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                chip_group.removeView(chip);
            }
        });
        chip_group.addView(chip);
    }
});
```
## AutoCompleteTextView
An AutoCompleteTextView only offers suggestion about the whole text. But `MultiAutoCompleteTextView` offers multiple suggestions for the substring of the text.
__Interact with Java:__
```
ArrayAdapter<String> adapter=new ArrayAdapter<String>(this,android.R.layout.simple_dropdown_item_1line,countries);
        AutoCompleteTextView textView=(AutoCompleteTextView)findViewById(R.id.autoComplete);
        textView.setThreshold(3);
        //  textViewM.setTokenizer(new MultiAutoCompleteTextView.CommaTokenizer());  // USED FRO MULTIAUTOCOMPLETETEXTVIEW
        textView.setAdapter(adapter);
```
- `setThreshold` - specify the number of characters after which the dropdown with the autocomplete suggestions list would be displayed. 

# View
Basic building block for user interface. 

It does not display any content on its own, it can be used as a placeholder, a separator, or a background element.

# Styling
## Shape
- `<solid>` tag specifies the fill color of the shape.
- `<stroke>` tag defines the border width and color.
- `<corners>` tag allows you to set the radius for rounded corners.
- `<padding>` tag specifies the padding inside the shape.
- `<size>` tag can define the width and height of the shape (useful for lines and rings).
- `<shape>` is the container tag, shape type is set by `android:shape` attribute along with shape tag
- `<gradient>` is used to define a gradient background

__Rectangle:__
```xml
<shape xmlns:android="http://schemas.android.com/apk/res/android">
    <solid android:color="#e9ecf3" />
    <corners android:radius="8dp" />
    <stroke android:width="2dp" android:color="#c0c0c0" />
    <padding android:left="10dp" android:top="10dp" android:right="10dp" android:bottom="10dp" />
</shape>
```
## Layer List
`<layer-list>` tag is used to define a list of layers (drawable objects) that are drawn on top of each other. It allows you to combine different drawable elements (such as shapes, gradients, images, etc.) into a single drawable.
```xml
<layer-list xmlns:android="http://schemas.android.com/apk/res/android">
    <item>
        <shape android:shape="rectangle">
            <stroke android:width="4dp" android:color="#ff0000"/>
        </shape>
    </item>
    <item
        android:left="30dp"
        android:drawable="@android:drawable/btn_plus"
        >
    </item>
</layer-list>
```
## Themes
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

Themes are applied to entire activities or applications, while styles are applied to individual views.
### Define a New Theme
```xml
<resources>
    <style name="themeName">
        <item name="viewAttribute">attributeValue</item>
    </style>
    <style name="anotherTheme" parent="themeName">
        <item name="colorPrimary">@color/primaryColor</item>
    </style>
</resources>
```
All the design from `themeName` inherited to `anotherTheme`.
### Apply Theme
__Application:__
Apply theme to the whole application with `<application>` tag and `android:theme` attribute.
```xml
<application android:theme="@style/themeName" ><application>
```
__Activity:__
Apply theme to a specific activity with `<activity>` tag and `android:theme` attribute.
```xml
<activity android:theme="@style/themeName" ><activity>
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
# Inflater
The primary purpose of LayoutInflater is to convert an XML layout file into a view object that can be used in your activity or fragment so that you can access it programmatically.

Each xml inside layout directory is not an activity. If it's an activity you can access it it by it's corresponding java file. But what about those file which is not an activity. There LayoutInflater comes, you can access those layout which are not an activity by LayoutInflater.

__LayoutInflater Instance:__
```
LayoutInflater inflater = getLayoutInflater();
//  LayoutInflater inflater = LayoutInflater.from(this);
```
__Inflating a Layout:__
```
View inflatedView = inflater.inflate(R.layout.my_layout, parent, false);
```
- `R.layout.my_layout` - The layout XML file which should be inflated.
- `parent` - The parent view where the inflated layout will be attached. If there have no parent use `null`.
- `false` - A boolean indicating whether to attach the inflated layout to the parent view immediately. Typically set to false when you intend to add the view programmatically.

__Access View:__
```
TextView textView = inflatedView.findViewById(R.id.custom_text);
```
# Toast
Toast isa lightweight way to display a short message to the user. It appears for a short duration and then disappears automatically. 
## Basic Usage
```
Toast.makeText(context, "Hello, Toast!", Toast.LENGTH_SHORT).show();
```
## Custom Toast
__Custom Layout for Toast:__
```
<LinearLayout android:id="@+id/customToast">
    <ImageView android:id="@+id/toast_icon" />
    <TextView android:id="@+id/toast_message" />
</LinearLayout>
```
__Inflate the custom layout for the Toast:__
```
LayoutInflater inflater = getLayoutInflater();
View layout = inflater.inflate(R.layout.custom_toast,(ViewGroup)findViewById(R.id.custom_toast_id));
```
__Create and show the Toast:__
```
Toast customToast = new Toast(MainActivity.this);
customToast.setDuration(Toast.LENGTH_LONG);
customToast.setGravity(Gravity.CENTER, 0, 0);
customToast.setView(layout);
customToast.show();
```
# Activity
Activity is a single screen with UI which serve as the entry point for user interaction with an app.

An activity is a class in Android that is designed to facilitate interaction between the user and the app. It typically consists of:

- `Layout (UI)`: The visual elements displayed to the user, defined in XML files.
- `Java/Kotlin Code`: The logic behind the activity, managing user interactions, data, and app functionality.

## Activity Lifecycle
Let's see the 7 lifecycle methods of android activity.
- `onCreate()`: Called when the activity is first created. Here, you typically initialize UI components and load essential data.
- `onStart()`: Called when the activity becomes visible to the user.
- `onResume()`: Called when the activity is ready to interact with the user.
- `onPause()`: Called when the activity loses focus but is still partially visible (e.g., when a dialog appears).
- `onStop()`: Called when the activity is no longer visible to the user.
- `onRestart()`: Called when the activity is restarted after being stopped.
- `onDestroy()`: Called before the activity is destroyed.

<img align="right" width="40%" src="https://static.javatpoint.com/images/androidimages/Android-Activity-Lifecycle.png" alt="masum184e" />
<pre>
    onCreate -> onStart -> onResume 
             <b>OTHER ACTIVITY</b> 
            onPause -> onStop
                <b>REOPEN</b> 
      onRestart -> onStart -> onResume
        <b>CLOSE APP, BACK BUTTON</b>
    onPause -> onStop -> onDestroy
</pre>

__Interact with Java:__
```
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_second);

    Toast.makeText(this, "SECOND ACTIVITY - CREATE", Toast.LENGTH_LONG).show();
}

@Override
protected void onStart(){
    super.onStart();
    Toast.makeText(this, "SECOND ACTIVITY - START", Toast.LENGTH_LONG).show();
}

@Override
protected void onResume(){
    super.onResume();
    Toast.makeText(this, "SECOND ACTIVITY - RESUME", Toast.LENGTH_LONG).show();
}

@Override
protected void onPause(){
    super.onPause();
    Toast.makeText(this, "SECOND ACTIVITY - PAUSE", Toast.LENGTH_LONG).show();
}

@Override
protected void onStop(){
    super.onStop();
    Toast.makeText(this, "SECOND ACTIVITY - STOP", Toast.LENGTH_LONG).show();
}

@Override
protected void onRestart(){
    super.onRestart();
    Toast.makeText(this, "SECOND ACTIVITY - RESTART", Toast.LENGTH_LONG).show();
}

@Override
protected void onDestroy(){
    super.onDestroy();
    Toast.makeText(this, "SECOND ACTIVITY - DESTROY", Toast.LENGTH_LONG).show();
}
```
- __Launching  :__ onCreate() -> load activity -> onStart() -> onResume()
- __Navigation :__ old activity -> onPause() -> current activity -> onCreate() -> load activity -> onStart() -> onResume() -> old activity -> onStop()
- __Home       :__ current activity -> onPause() -> onStop()
- __Recents    :__ remove app from recents -> onDestroy()
# Intent
Intent class is used to navigate through activity. Intent class accept two parameter, first one is current activity, and another one is navigated activity.
```
Intent intent = new Intent(this, SecondActivity.class);
startActivity(intent);
```
## Bundle
`Bundle` is a collection of key-value pairs that is used to pass data between different components of an application such as between activities, fragments. It's a convenient way to package and transmit data because it can hold a variety of data types including primitive types, strings, arrays and even custom parceable objects.

## Pass Data Between Activity
__Send:__ `intent.putExtra()` - is used to send extra data with key value pair
```
intent.putExtra("EXTRA_MESSAGE", "Hello from MainActivity!");
```
__Recieve:__ `getIntent()` and `getStringExtra()` - is used to retreive data from activity
```
Intent intent = getIntent();
String message = intent.getStringExtra("EXTRA_MESSAGE","DEFAULT_VALUE);
```
## Navigation
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
# Fragment
Fragment represents a reusable portion of your application's user interface. It is similar to activity but can't run by independently, it needs help of activity. It is child of activity.

For 3-5 fragments use TabLayout, for 5-7 fragments use BottomNavigation, for more than 7 fragments use NavigationDrawer.

Fragments have their own lifecycle, which is closely tied to the lifecycle of the host activity.
- `onAttach()` 
- `onCreate()` 
- `onCreateView()` 
- `onActivityCreated()` 
- `onStart()` 
- `onResume()` 
- `onPause()` 
- `onStop()` 
- `onDestroyView()` 
- `onDestroy()` 
## Static Fragment
1. __Fragment Class:__
Create a fragment by extending the Fragment class and overriding key lifecycle methods.
```
@Override
public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState) {
    return inflater.inflate(R.layout.fragment_frag_a, container, false);
}
```
2. __Fragment Layout:__
By default, FrameLayout is the default layout. But you can use any of the layout to create fragment.
3. __Merge with Activity:__
`<fragment>` tag and `name` attribute is used to statically add a fragment to an activity.
```
<fragment android:name="com.example.project_name.fragment_name" />
```
__Handle Fragment:__
```java
public View onCreateView(LayoutInflater inflater, ViewGroup container Bundle savedInstanceState) {
    View view=inflater.inflate(R.layout.fragment_frag_a, container, false);
    Button btn= view.findViewById(R.id.button);
    btn.setOnClickListener(new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            Toast.makeText(getContext(), "Fragment A", Toast.LENGTH_LONG).show();
        }
    });

    return view;
}
```
## Dynamic Fragment
Just instead using `<fragment>` tag, handle it programmitically.
```java
FragmentManager fragmentManager=getSupportFragmentManager();
fragmentManager.beginTransaction().replace(R.id.layout_contaner, new BlankFragment()).commit();
```
- `layout_container` - where fragment should stay.
- `BlankFragment` - class name of new fragment.
# Bottom Navigation
__1. Menu Resource File:__
```xml
<menu>
    <item />
    <item />
</menu>
```
__2. Fragment:__ Create fragment for each of the item.

__3. XML Layout:__
```xml
<FrameLayout
    android:id="@+id/layout_container"
    android:layout_height="0dp"
    android:layout_weight="1"
    />
<com.google.android.material.bottomnavigation.BottomNavigationView
    android:id="@+id/bottomNavigation"
    android:layout_height="60dp"
    app:menu="@menu/menu_main"
    />
```
__4. Handling Item Selection:__
```java
bottomNavigation.setOnItemSelectedListener(new NavigationBarView.OnItemSelectedListener() {
    @Override
    public boolean onNavigationItemSelected(@NonNull MenuItem menuItem) {
        int currentItemId=menuItem.getItemId();

        if(currentItemId==R.id.action_save)load_fragment(new FragmentA());
        else if(currentItemId==R.id.action_manage)load_fragment(new FragmentB());
        else if(currentItemId==R.id.action_home)load_fragment(new FragmentC());
        else if(currentItemId==R.id.action_places)load_fragment(new FragmentD());
        else load_fragment(new FragmentE());

        return true;
    }
});
bottomNavigation.setSelectedItemId(R.id.action_save);
```

- `bottomNavigation.setSelectedItemId(R.id.action_save);` - set the inital fragment
- `return true` - set the active design of selected menu item
# Actionbar
It is a standard component provided by the `Android framework` that sits at the top of an activity window.  It typically displays the activity’s title, navigation options (like the back button). Automatically provided by Android when you use a theme that supports an ActionBar (e.g., Theme.AppCompat.Light.DarkActionBar).

## Basic Usage
1. __Set up The Theme:__
The activity or the whole application, where toolbar should be implement must contain a theme that support an ActionBar.

    - `android:label` attribute from `<application>` tag or `<activity>` tag is the default label of toolbar.

2. __Java__
```java
ActionBar actionBar = getSupportActionBar();
if (actionBar != null) {
    actionBar.setTitle("My Title");
    actionBar.setSubtitle("My Subtitle");
    actionBar.setDisplayHomeAsUpEnabled(true);
}
```
- `setDisplayHomeAsUpEnabled` - display a back arrow which navigates up in the application's hierarchy.
- `return true;` - means that you have handled the menu item selection.
- `return false;` - indicates that you have not handled the event, and the system should continue to process it(rare);
- `return super.onOptionsItemSelected(item);` - allow the superclass to handle the event.
## Custom Actionbar
```java
ActionBar actionBar = getSupportActionBar();
if (actionBar != null) {
    actionBar.setDisplayHomeAsUpEnabled(true);
    actionBar.setDisplayShowCustomEnabled(true);
    actionBar.setCustomView(R.layout.custom_actionbar);
}
```
## Back Button
```java
@Override
public boolean onOptionsItemSelected(MenuItem item) {
    int id = item.getItemId();

    if (id == android.R.id.home) {
        Fragment currentFragment = getSupportFragmentManager().findFragmentById(R.id.fragment_container);

        if (currentFragment instanceof HomeFragment) {
            return true;
        } else {
            getOnBackPressedDispatcher().onBackPressed();
            return true;
        }
    }

    return super.onOptionsItemSelected(item);
}
```
## Menu Items
__Displaying 3 dots in right side of actionbar:__
```java
@Override
public boolean onCreateOptionsMenu(Menu menu) {
    MenuInflater inflater = getMenuInflater();
    inflater.inflate(R.menu.menu_main, menu);
    return true;
}
```
__Handling click event on each menu item:__
```java
@Override
public boolean onOptionsItemSelected(@NonNull MenuItem item) {
    int id = item.getItemId();

    // Handle 3-dot menu items
    if (id == R.id.action_manage) {
        Toast.makeText(this, "Manage clicked!", Toast.LENGTH_SHORT).show();
        return true;
    } else if (id == R.id.action_save) {
        Toast.makeText(this, "Save clicked!", Toast.LENGTH_SHORT).show();
        return true;
    } else if (id == R.id.action_home) {
        Toast.makeText(this, "Home clicked!", Toast.LENGTH_SHORT).show();
        return true;
    }

    return super.onOptionsItemSelected(item);
}
```
## Toolbar
It is a ViewGroup that can be added to any part of your layout and can act as a complete replacement for the ActionBar.

Toolbar can replace the ActionBar. By using the `setSupportActionBar(Toolbar toolbar)` method in an `AppCompatActivity`, you can promote a Toolbar to act as the app’s ActionBar.
```java
setSupportActionBar(toolbar);
```
# Logging
It allow developers to track the flow of their application, debug issues, and monitor behavior during runtime. Android provides a built-in logging framework through the `android.util.Log` class, which allows developers to output log messages of varying severity levels.

## Log Levels
1. __Error:__ Used to log error conditions that might cause the application to crash or behave unexpectedly(`catch` block).
2. __Warning:__ Used to indicate potential issues that do not prevent the application from functioning but should be addressed.
3. __Info:__ Used for informational messages that highlight the progress of the application. These messages can be useful for tracking significant application events. It uses to display the system message.
4. __Debug:__ Used for debugging messages. These messages are useful during development but will be disabled in production builds.
5. __Verbose:__ The least important level, typically used for providing detailed information during debugging.
6. __Assert:__ Used to log assertions, indicating conditions that should never occur. This level is typically used for critical errors.

## Logging Methods

`Log.v()`,`Log.d()`,`Log.i()`,`Log.w()`,`Log.e()`,`Log.wtf()` is used for verbose, debug, informational,  warning, error, assertion message respectively. Each method required a tag and log message. Debugging and Error are most of the uses methods.

__Example:__
```java
Log.i("TAG","MESSAGE")
```
## Message Format
__Syntax:__ `date time PID-TID package application_name priority tag:message`
- `PID` - Process ID
- `TID` - Thread ID
__Example:__
```
2024-08-19 13:42:14.215 17520-17547 ProfileInstaller        com.example.learning                 D  Installing profile for com.example.learning
```
- `2024-08-19` - date
- `13:42:14.215` - time
- `17520` - PID
- `17547` - TID
- `ProfileInstaller` - Application ame
- `com.example.learning` - package
- `D` -priority
- `Installing profile for com.example.learning` - message
# Database
## SharedPreferences
It is used for storing small amounts of primitive data in key-value pairs. You can use it for storing user setting, last score, location caching

__Store Data:__
```java
SharedPreferences sharedPreferences = getSharedPreferences("MyPreferences", Context.MODE_PRIVATE);
SharedPreferences.Editor editor = sharedPreferences.edit();
editor.putString("key", "value");
editor.putInt("key", 123);
editor.apply();  // or editor.commit();
```
__Retrieve Data:__
```java
SharedPreferences sharedPreferences = getSharedPreferences("MyPreferences", Context.MODE_PRIVATE);
if(sharedPreferences.contains("key")){
  String value = sharedPreferences.getString("key", "default_value");
  int number = sharedPreferences.getInt("key",123);
}
```
__Update Data:__ Updating data is same as inserting it.

__Delete Data:__
```java
SharedPreferences sharedPreferences = getSharedPreferences("MyPreferences", Context.MODE_PRIVATE);
SharedPreferences.Editor editor = sharedPreferences.edit();
editor.remove("key");
editor.apply();
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
# Retrofit
Enable internet permissoin.
```
<uses-permission android:name="android.permission.INTERNET" />
```
Update Dependency
```
dependencies {
    implementation 'com.squareup.retrofit2:retrofit:2.9.0'
    implementation 'com.squareup.retrofit2:converter-gson:2.9.0'
}
```
## GET
### Define API endpoints
Define the endpoints in `java/com.example.project_name/data/ApiService.java` file.
```java
public interface ApiService {
    @GET("posts")
    Call<List<PostRequest>> getAllPosts();
}
```
### Define data model
Define the data models in `java/com.example.project_name/models/PostRequest.java` file.
```java
public class PostRequest {
    private String title;
    private String body;
    
}
// Getters and Setters Method
```
### Make the call
Call the API asynchronously and handle the response or failure.
```java
Retrofit retrofit = new Retrofit.Builder()
        .baseUrl("https://jsonplaceholder.typicode.com/")
        .addConverterFactory(GsonConverterFactory.create())
        .build();

ApiService apiService = retrofit.create(ApiService.class);

Call<List<PostRequest>> call = apiService.getAllPosts();

call.enqueue(new Callback<List<PostRequest>>() {
    @Override
    public void onResponse(Call<List<PostRequest>> call, Response<List<PostRequest>> response) {
        if (response.isSuccessful()) {
            List<PostRequest> posts = response.body();
            for (PostRequest post : posts) {
                Log.d("Retrofit", "Post Title: " + post.getTitle());
            }
        } else {
            Log.e("Retrofit", "Request failed. Code: " + response.code());
        }
    }

    @Override
    public void onFailure(Call<List<PostRequest>> call, Throwable t) {
        Log.e("Retrofit", "Request failed. Error: " + t.getMessage());
    }
});
```
### Make the call with id
1. __Update the endpoint__
```java
@GET("posts/{id}")
Call<PostRequest> getPost(@Path("id") int postId);
```
2. __Update the call__
```java
Call<PostRequest> call = apiService.getPost(1);

call.enqueue(new Callback<PostRequest>() {
    @Override
    public void onResponse(Call<PostRequest> call, Response<PostRequest> response) {
        if (response.isSuccessful()) {
            PostRequest post = response.body();
            Log.d("Retrofit", "Post Title: " + post.getTitle());
        } else {
            Log.e("Retrofit", "Request failed. Code: " + response.code());
        }
    }

    @Override
    public void onFailure(Call<PostRequest> call, Throwable t) {
        Log.e("Retrofit", "Request failed. Error: " + t.getMessage());
    }
});
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
### Accessing ActionBar
```
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