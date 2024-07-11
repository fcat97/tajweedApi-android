![cover image](https://github.com/fcat97/TajweedApi/blob/main/doc/cover.png?raw=true)

# Tajweed Api

An android library to add tajweed colors into arabic texts. 

## What's New?

- Custom color for rules now supported.
- Custom implementation of tajweed rules.
- Platform specific method deprecated.
- Matching tajweed along with its type and position.
- Initial refactor for supporting multiplatform.

## Add To Project

**Step 1.** Add the JitPack repository to your build file

Add it in your root build.gradle at the end of repositories:

```gradle
allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
}
```

**Step 2.** Add the dependency. `version:` [![](https://jitpack.io/v/fcat97/tajweedApi-android.svg)](https://jitpack.io/#fcat97/tajweedApi-android)

```gradle
dependencies {
    implementation 'com.github.fcat97:tajweedApi:version'
    implementation 'com.github.fcat97:tajweedApi-android:version'
}
```

**Step 3.** Now to use 
```kotlin
val verse = "خَتَمَ ٱللَّهُ عَلَىٰ قُلُوبِهِمْ وَعَلَىٰ سَمْعِهِمْۖ وَعَلَىٰٓ أَبْصَٰرِهِمْ غِشَٰوَةٌۖ وَلَهُمْ عَذَابٌ عَظِيمٌ" // sura bakarah 2:7
val api = IndoPakTajweedApi.getSingleton()
val result = api.getTajweed(verse)

val painter = AndroidIndoPakPainter()
painter.paint(SpannableString(verse), result, DefaultIndopakColor)
```

## Migration Guide

### From v1.0.x to v2.0.0

instead of using `TajweedApi.getTajweedColored(verse)`, use an implementation of `TajweedApi`.
A default implementation is `IndoPakTajweedApi` which is gives the same result as the older one.
If you want to use it as a singleton the the previous, use `IndoPakTajweedApi.getSingleton().getTajweedColored(verse)` instead.