StickyScrollViewItems
=====================
StickyScrollViewItems is a `ScrollView` subclass that allowed you to mark items inside the `ScrollView` as `sticky`. The items marked as sticky will stick to the top of the `ScrollView` until another `sticky` items comes by and pushes it out of the way.

Installing
----------
Add the following gradle dependency exchanging x.x.x for the latest release.
```groovy
dependencies {
    compile 'se.emilsjolander:StickyScrollViewItems:x.x.x'
}
```

Usage
-----
First of all replace any instance of `ScrollView` with `StickyScrollView`.
So you go from this:
```xml
<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
	android:layout_height="match_parent" android:layout_width="match_parent">
	<!-- scroll view child goes here -->
</ScrollView>
```
to this:
```xml
<StickyScrollView xmlns:android="http://schemas.android.com/apk/res/android"
	android:layout_height="match_parent" android:layout_width="match_parent">
	<!-- scroll view child goes here -->
</StickyScrollView>
```

As with a regular `ScrollView` you are only allowed one child. But that child can contain any number of children. It is these children or any of their children that can be tagged as a sticky view. If you want t view to stick to the top when you scroll passed it add a `sticky` tag with the `android:tag` attribute to it like this:
```xml
<StickyScrollView xmlns:android="http://schemas.android.com/apk/res/android"
	android:layout_height="match_parent" android:layout_width="match_parent">

	<LinearLayout 
		android:layout_height="match_parent" android:layout_width="match_parent" 
		android:orientation="horizontal">

		<!-- other children -->

		<View 
			android:layout_height="300dp" 
			android:layout_width="match_parent"
			android:tag="sticky"/>

		<!-- other children -->

	</LinearLayout>

</StickyScrollView>
```

There are also two additional flags that can be set on views that were added to optimize performance for the most usual cases. If the view you want to stick either has transparency or does not have a constant representation than you must supply one or both of the following flags. `-hastransparancy` for views that have transparancy and `-nonconstant` for views that will change appearance during there sticky time (examples are buttons with pressed states as well as progress spinners).

So this ends up with 4 different ways to tag a view as sticky resulting is slightly different behaviour `android:tag="sticky"` `android:tag="sticky-hastransparancy"` `android:tag="sticky-nonconstant"` and `android:tag="sticky-hastransparancy-nonconstant"`.
