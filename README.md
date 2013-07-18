Ark
===

This is a central GitHub powered maven repo for android .aar and .jar files for
use as dependencies in Android projects with the new Gradle Build Tool.

Why jump through hoops for Maven Central when you can publish right on GitHub?

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
    compile 'com.actionbarsherlock:actionbarsherlock:4.3.1'
}
```

Adding your own library to Ark
------------------------------

### By Updating your library and filing an issue:
* Add something like this to your build.gradle:
  ```
  apply plugin: 'maven-publish'

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
  Make sure it generates the ark/releases folder _next_ to your git
  repository, _not_ inside it. So add/remove `../` as necessary.
* File an issue, I'll get to it, or tell you you're doing it wrong.

### By Pull Request:
* Fork this repo
* Publish your library into your forked repo (see example `build.gradle` section from above)
* Open a pull request
