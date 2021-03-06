## GlideWebpDecoder

GlideWebpDecoder is a [Glide](https://github.com/bumptech/glide) integration library for decoding and displaying webp images on Android platforms. It is based on [libwebp](https://github.com/webmproject/libwebp) project and takes some implementation from [Fresco](https://github.com/facebook/fresco) and [GlideWebpSupport](https://github.com/roths/GlideWebpSupport) as references.

## Features

* play animated webp images on all Android versions
* show transparent or lossless webp images on Android devices lower than 4.2.1 (BitmapFactory support webp decode on 4.2+ android system so we have no need to handle)

## Dependency Integration

Library is available in jcenter. If you are build with Gradle, just add the following dependencies to your `build.gradle` file.
Different Glide version is corresponding to different GlideWebpDecoder due to the annotation processor compatibility. The version rule of GlideWebpDecoder is "{major_version}.{glide_version}".
For example, if you use glide 4.7.1, the corresponding version of GlideWebpDecoder should be 0.0.8.4.7.1

Library will only follow the latest three version of Glide. If you use a lower version glide, please clone the project and modify it yourself.

Glide 4.7.0 is not available in maven, see [issue 3015](https://github.com/bumptech/glide/issues/3015)

Glide 4.6.0 is broken, see [issue 2863](https://github.com/bumptech/glide/issues/2863)

```gradle
def GLIDE_VERSION = "4.7.1"
// webpdecoder
compile "com.zlc.glide:webpdecoder:0.0.8.${GLIDE_VERSION}"
// glide 4.5.0~4.7.1 (exclude broken version 4.6.0, 4.7.0)
compile "com.github.bumptech.glide:glide:${GLIDE_VERSION}"
annotationProcessor "com.github.bumptech.glide:compiler:${GLIDE_VERSION}"
```

Then you are free to use GlideWebpDecoder just like use other Glide integration library.

## Proguard

The library use native code to decode webp, so you should put the following lines to your `proguard.cfg` and keep the jni interface.

```pro
-keep public class com.bumptech.glide.integration.webp.WebpImage { *; }
-keep public class com.bumptech.glide.integration.webp.WebpFrame { *; }
-keep public class com.bumptech.glide.integration.webp.WebpBitmapFactory { *; }
```

## Acknowledgement

* [libwebp](https://github.com/webmproject/libwebp)
* [Fresco](https://github.com/facebook/fresco)
* [GlideWebpSupport](https://github.com/roths/GlideWebpSupport)

## License

The Library is [Apache-2.0-licensed](https://github.com/zjupure/GlideWebpDecoder/blob/master/LICENSE), part code is [MIT-licensed](https://github.com/facebook/fresco/blob/master/LICENSE) see [Fresco](https://github.com/facebook/fresco) for detail.

