Ark
===

This is a central GitHub powered maven repo for android .aar and .jar files for
use as dependencies in Android projects with the new Gradle Build Tool.

Why jump through hoops for Maven Central when you can publish right on GitHub?

This is currently my personal collection of common libraries that I forked and published
myself. If you like it or want to add to it please contribue!

Usage
-----

To use, add this github repo as a repository:
```
repositories {
    maven {
        url 'https://raw.github.com/ark/ark/master/releases/'
    }
}
```

Then add the libraries you want as dependencies:

```
dependencies {
    compile 'com.actionbarsherlock:actionbarsherlock:4.4.0'
}
```

Adding your own library to Ark
------------------------------

### By Updating your library and filing an issue:
* Add something like this to your build.gradle (currently only works with android plugin 0.5.4):
  ```
  apply plugin: 'maven-publish'

  group = 'com.example`
  version = '1.0.0'

  android.libraryVariants
  publishing {
      publications {
          maven(MavenPublication) {
             artifact bundleRelease
          }
      }
      repositories {
          maven {
              url "file://$buildDir/../../ark/releases"
          }
      }
  }
  ```
  Make sure the maven repo url points to the ark/releases folder inside
  the ark repository, _not_ inside the project being built. So add/remove `../`
  or change the url as necessary.
* File an issue, I'll get to it, or tell you you're doing it wrong.

### By Pull Request:
* Fork this repo
* Publish your library into your forked repo (see example `build.gradle` section from above)
* Open a pull request


### Currently available packages:

#### Releases:
*  `com.actionbarsherlock:actionbarsherlock:4.3.1`
*  `com.actionbarsherlock:actionbarsherlock:4.4.0`
*  `com.viewpagerindicator:library:2.4.1`
*  `com.loopj.android.http:android-async-http:1.4.3`
*  `de.keyboardsurfer.android.widget:crouton:1.8.1`
*  `com.makeramen:roundedimageview:1.0.0`
*  `com.astuetz:pagerslidingtabstrip:1.0.0`

#### Snapshots

*  `com.actionbarsherlock:actionbarsherlock:4.3.2-SNAPSHOT`
*  `com.loopj.android.http:android-async-http:1.4.4-SNAPSHOT`
*  `de.keyboardsurfer.android.widget:crouton:1.8.2-SNAPSHOT`
*  `com.android.frameworks:volley:master-SNAPSHOT`
*  `com.romainguy:viewserver:1.0-SNAPSHOT`
*  `com.astuetz:pagerslidingtabstrip:1.0.0-SNAPSHOT`

Open an issue or contact me if you want any packages added to this repo!
