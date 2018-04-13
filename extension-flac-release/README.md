Make sure you follow the extensions build guide in `ExoPlayer` for flac.

Essentially extract the flac src into `ExoPlayer/extensions/flac/src/main/jni/flac`
Then at `ExoPlayer/extensions/flac/src/main/jni` level, run:
```
> ndk-build APP_PLATFORM=android-11 -j4
```
and wait for all the `.so` files to build. Check `flac/src/main/libs` to see if there are any `.so`
files under each architecture.

Then at `ExoPlayer` level, run:
 ```
 > ./gradlew assembleWithExtensions
 ```
And the `extension-flac-release.aar` should appear at `ExoPlayer/extensions/flac/buildout/output/aar`
It should have a size around 900KB. If it's smaller, you probably forgot to compile the native `.so`
libraries.
