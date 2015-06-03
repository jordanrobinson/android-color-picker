# Android Color Picker

The AOSP color picker, neatly packaged for gradle builds

## What is it

Android color picker is the stock color picker that comes bundled in a few apps distributed by Google, with the calendar app being the main example. It allows you to specify a list of colors, show the user a dialog, and get the result. Nice and simple.

![example-use](https://cloud.githubusercontent.com/assets/1202911/6986937/2475346e-da3a-11e4-99c5-0aeb3a0bcaa7.gif)

## Why is it here?

I needed a color picker for Android, the stock color picker was exactly what I wanted, but grabbing the source, compiling down and using a local repositry compiled to an AAR is nowhere near as fun as a Gradle dep.

## How do I use it

In your build file:

	compile 'uk.co.jordanrobinson:android-color-picker:1.0.1'


in your layout:

    <Button
        android:id="@+id/color_picker"
        android:layout_width="fill_parent"
        android:layout_height="60dip"
        android:onClick="showColourPicker"
        android:text="Pick a colour!"
        android:gravity="center" />

in your activity:

	import com.android.colorpicker.ColorPickerDialog;
	import com.android.colorpicker.ColorPickerSwatch;

    public void showColourPicker(View view) {
        final ColorPickerDialog colorPickerDialog = new ColorPickerDialog();
        colorPickerDialog.initialize(R.string.color_picker_default_title,
                new int[] {
                        getResources().getColor(R.color.GlobalColorDark),
                        getResources().getColor(R.color.ThemeOneDark),
                        getResources().getColor(R.color.ThemeTwoDark),
                        getResources().getColor(R.color.ThemeThreeDark),
                        getResources().getColor(R.color.ThemeFourDark),
                        getResources().getColor(R.color.ThemeFiveDark),
                        getResources().getColor(R.color.ThemeSixDark),
                        getResources().getColor(R.color.ThemeSevenDark),
                        getResources().getColor(R.color.ThemeEightDark),
                        getResources().getColor(R.color.ThemeNineDark),
                        getResources().getColor(R.color.ThemeTenDark),
                        getResources().getColor(R.color.ThemeElevenDark),
                }, getResources().getColor(R.color.ThemeOneDark), 3, 2);

        colorPickerDialog.setOnColorSelectedListener(new ColorPickerSwatch.OnColorSelectedListener() {
            @Override
            public void onColorSelected(int colour) {
                YourActivity.this.setYourFragmentBackgroundColour(colour);
            }
        });

        android.app.FragmentManager fm = this.getFragmentManager();
        colorPickerDialog.show(fm, "colorpicker");
    }

And you're good to go!

## When will it update?

If there are bugs and fixes that come from downstream, I'll update if I notice them myself, or if anyone raises an issue I'll do my best to keep up.

Contributions are of course always welcome, but to avoid disappointment, send me a message if you're making any radical changes to make sure it's the kind of thing I'm expecting. Thanks!

I'm not going to rule out new features coming from me, but at present they aren't really needed by me. Feel free to submit requests though!

## Who did this?
[That would be me.](http://jordanrobinson.co.uk)
