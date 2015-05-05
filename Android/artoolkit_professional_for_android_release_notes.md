# ARToolkit Professional for Android Release Notes

Latest release: 17.

README
------

    Supplementary read me for ARToolKit Professional for Android, release 17.
    =========================================================================


    Contents.
    ---------

    About this archive.
    Requirements.
    Getting started.
    Training new markers.
    Release notes.
    Next steps.


    About this archive.
    -------------------

    This archive contains the ARToolKit Professional libraries, utilities and
    examples for Android, release 17.

    ARToolKit Professional for Android is released to you under a proprietary
    license. Please note that your license terms impose various restrictions on
    distribution of ARToolKit in both source and binary forms. Legal remedy will be
    sought by ARToolworks, Inc. for any unauthorised distribution. Please do not
    attempt to publish your app on Google's Play Store or any other commercial
    marketplace until you have obtained a valid license from ARToolworks.

    This archive was assembled by:
        Philip Lamb
        ARToolworks, Inc.
        http://www.artoolworks.com
        2014-01-06


    Requirements.
    -------------

    Requirements:
     * Android SDK Tools r12 (for Android 2.2/API 8) or later required, r22 (July
    2013) or later recommended.
     * Development of native ARToolKit for Android applications or requires Android
    NDK Revision 5 or later, revision 9 (July 2013) recommended.
     * Use of the Eclipse IDE is recommended, and Eclipse project files are supplied
    with the ARToolKit for Android SDK.
     * An Android device, running Android 2.2 or later. Testing is not possible
    using the Android Virtual Device system.
     * A printer to print the pattern PDF images.

    ARToolKit Professional for Android differs from ARToolKit for other platforms,
    in that most of the libraries are supplied in binary-only SDK form, with
    additional source for the examples. If you wish to experiment further with
    ARToolKit techniques (beyond those provided in the examples) you will also need
    to use this Android release alongside a regular full release of ARToolKit
    Professional v5.x for Mac OS X, Windows, or Linux.


    Getting started.
    ----------------

    For full instructions on using this SDK, please refer to the online user guide
    at http://www.artoolworks.com/support/library/ARToolKit_for_Android.


    Training new markers.
    ---------------------

    The utilities required to train new square and NFT markers are provide in the
    "bin" directory of the SDK. The utilities are command-line Windows/Mac OS X
    executables which should be run from a Terminal environment.

    Consult the ARToolworks support library for more information:
        http://www.artoolworks.com/support/library/
    Creating_and_training_new_ARToolKit_markers
        http://www.artoolworks.com/support/library/ARToolKit_NFT

    Usage (Mac):
        ./mk_patt
        ./genTexData somejpegfile.jpg
        ./dispImageSet somejpegfile.jpg
        ./dispFeatureSet somejpegfile.jpg
        ./checkResolution Data/camera_para.dat (change camera_para.dat to the
    correct camera calibration file for your device, camera and resolution).

    Usage (Windows):
        mk_patt.exe
        genTexData.exe somejpegfile.jpg
        dispImageSet.exe somejpegfile.jpg
        dispFeatureSet.exe somejpegfile.jpg
        checkResolution.exe Data/camera_para.dat (change camera_para.dat to the
    correct camera calibration file for your device, camera and resolution).


    Release notes.
    --------------
    This release contains ARToolKit Professional v5.0.5 for Android. Please see the
    ChangeLog.txt for details of changes in this and earlier releases.

    The following major changes in ARToolKit version 5 are discussed in detail
    below:
    *   New NFT dataset format.
    *   Support for optimised bi-planar video formats.
    *   OpenGL ES 2.0 support.
    *   Improved support for stereo and see-through displays.

    * New NFT dataset format *

    ARToolKit version 5.0 introduces a new (non-backwards compatible) improved NFT
    dataset format. While most of the APIs and tools for NFT tracking remain
    identical, performance has been improved and dataset sizes have been
    dramatically reduced, typically by more than 90%. As an example, the “pinball”
    sample NFT dataset (high-resolution A4 size) included with ARToolKit v4.x has
    shrunk from a total of 4.4MB to 324KB. An A5-size dataset at lower resolution
    can be shrunk to under 100KB. This change comes with the same level of tracking
    performance. We believe this will make both local storage and over-the-air
    transmission of NFT datasets far more comfortable for developers.

    To take advantage of the new format, upgrade your application code to the sample
    code included with ARToolKit v5, link against the new version of the ARToolKit
    libraries, and re-run your dataset generation on the same original images.

    * Support for optimised bi-planar video formats *

    The capture, processing and display of video from the camera is a significant
    load on a typical AR application. That’s why we’ve put a lot of effort into
    improving performance in this area, especially on iOS and Android. Full support
    for optimised bi-planar YCbCr image formats is now throughout the toolkit,
    including acquisition by libARvideo, processing by libAR, libAR2 and libKPM, and
    display by libARgsub_es. The result is lower I/O, CPU and memory bus bandwidth
    requirements, reduced memory usage, improved tracking performance, and
    consequent reduced CPU usage and improved battery life on mobile devices.

    The default format for iOS apps is now AR_PIXEL_FORMAT_420f, and for Android
    apps AR_PIXEL_FORMAT_NV21. If developers still need RGBA pixels, e.g. for
    screen-capture purposes, it is trivial to request this instead with the
    “-format=” video configuration string token.

    * OpenGL ES 2.0 support *

    Support for OpenGL ES 2.0 has been added… finally! A new version of the GL
    integration library, libARgsub_es2, provides support for video see-through
    rendering, and utility functions to support a programmable OpenGL pipeline
    including shader management and matrix manipulation. The iOS app ARApp and the
    Android app ARNative have been updated to ES2, while the same apps are also
    available targeting ES1 (as ARAppES1 and ARNativeES1, respectively) to allow
    developers to compare and contrast the changes required.

    Further ES2 support will progressively be added to the toolkit, including in the
    OSG-based examples, and the glm renderer. However, the new support provides the
    groundwork for developers to use ES 2 or integrate their existing ES 2-based
    code into an ARToolKit-based app.

    * Improved support for stereo and see-through displays *

    One of the strengths of ARToolKit is its adaptability to a wide range of
    different hardware configurations. ARToolKit has for some time been unique in
    its support for tracking with stereo cameras. In version 5, as well as
    continuing to support ARToolKit’s stereo tracking, the stereo example now
    supports a variety of different stereo display configurations, including:
    dual-output, quadbuffered/frame-sequential, side-by-side, over-under (and
    half-width/half-height variants), and more.

    ARToolKit’s support for see-through head-mounted displays (HMDs) is greatly
    improved in ARToolKit version 5 too. The calib_optical utility has been made
    easier to use, and can also be used with stereo see-through HMDs while tracking
    with a single camera. The optical and stereoOptical examples also now provide
    high-quality rendering via OSG.

    * For much more detail of changes in this and earlier releases please see the
    file ChangeLog.txt. *


    Next steps.
    -----------

    We have made a forum for discussion of AR for Android development available on
    our community website.

    http://www.artoolworks.com/community/forum/viewforum.php?f=26

    You are invited to join the forum and contribute your questions, answers and
    success stories.

    ARToolKit consists of a full ecosystem of products for desktop, web, mobile and
    in-app plugin augmented reality. Stay up to date with information and releases
    from ARToolworks by joining our announcements mailing list.

    http://www.artoolworks.com/Announcements_mailing_list.html



    --
    EOF

ChangeLog
---------

    ARToolKit Professional ChangeLog.
    =================================

    Changes in version 5.0.5 (this release) (2014-01-06).
    -----------------------------------------------------
    Enhancements:
    - arImageProcMode is now exposed through libARWrapper.
    - Numerous small API documentation improvements.
    - EdenSound interface is now provided, connecting to OpenAL.
    - Android: the CameraPreferences API now allows querying of whether the camera
    is front-facing.
    - Added arUtilGetFileExtensionFromPath().
    - In threading library, added extra function threadGetBusyStatus to test if a
    thread is between start and end states.
    - gluttext is now in libEden.
    - calib_camera will use arImageProcLuma to do grayscale conversion, improving
    performance.
    - Added a parameter to arImageProcInit to force copying of incoming image, even
    if mono, to handle case where we might need to keep the image around for longer.
    - ARWrapper internal improvements.
    - Windows: The DSVideoLib library (used with video config '-device=DSVL') has
    been recompiled with VS 2010 SP1. There should no longer be any need to include
    msvsr71.dll or msvcp71.dll with ARToolKit-based applications, and these files
    have been removed from the installed version of ARToolKit.

    Bug fixes:
    - The tool for generating NFT datasets, genTexData, now enforces a lower limit
    of 196 pixels square on the smallest image in the image set. This corrects an
    error which occured during KPM data creation when small images were used.
    - A bug in eliminating marker matches with low confidence values when using
    mixed pattern/barcode detection mode has been corrected.
    - iOS examples: Removed an extraneous -drawView call from EAGLView's
    -layoutSubviews method.
    - genTexData now allows generation of a dataset with a single resolution
    (provide the same value for min and max DPI).
    - Include API reference for ARWrapper in release package.
    - Ensure all glStateCache(En/Dis)AbleTex2D calls are proceeded by
    glStateCacheActiveTexture() and all
    glStateCache(Dis/En)ableClientStateTexCoordArray calls are proceeded by
    glStateCacheClientActiveTexture().
    - Don't require ARParam to be kept around for lifetime of
    ARGL_CONTEXT_SETTINGS_REF.


    Changes in version 5.0.4 (2013-10-17).
    --------------------------------------
    New features:
    - This release includes libARWrapper (previously known as libARToolKitWrapper)
    which was previously supplied only with ARToolKit for Android. As ARWrapper has
    utility as a generic simplified C API to ARToolKit (for example when binding to
    Java or C#) it will now be provided for all platforms.
    - Full source code for the NFT utilities is now provided. This will allow
    customisation of the NFT dataset generation.

    Bug fixes:
    - mtxRotatef()/mtxRotated() (included in <AR/gsub_mtx.h>) now correctly
    normalise a non-normal axis of rotation. Previously, rotations were incorrect if
    the axis was not normalised.


    Changes in version 5.0.3 (2013-10-07).
    --------------------------------------
    Enhancements:
    - This release adds support for the iPhone 5s and 5c.


    Changes in version 5.0.2 (2013-10-04).
    --------------------------------------
    Bug fixes:
    - The glm model loader for Wavefront .obj files now better handles non-standard
    .obj files. Additionally, an option has been provided to flip textures on .obj
    files in the vertical dimension, as many .obj models are written with textures
    flipped. To enable texture flipping for a single .obj model, add this line to
    the model definition in the models.dat file: "CONFIG TEXTURE_FLIPV" (without the
    quotes).
    - iOS: Fixed a problem building EAGLView on the pre-iOS 7 SDK (added inclusion
    of QuartzCore headers).
    - iOS: Fixed a problem in ARViewController which lead to the ARView not being
    released when the view controller was disposed of.

    Enhancements:
    - This release updates the included OpenCV libraries to version 2.4.6.1 (on
    Windows, OS X, and Linux).


    Changes in version 5.0.1 (2013-09-18).
    --------------------------------------
    Bug fixes:
    - A bug in handling of frame-sequential stereo has been corrected. Note that
    frame-sequential stereo generally requires a fixed frame rate, which is not
    guaranteed by GLUT. Platform-specific window-handling code will be added in a
    future release.
    - NFT input images are required to have an even number of pixels in both width
    and height. A check has been added to genTexData to enforce this.
    - Handling of file extensions in readtex() (used on iOS and Android) is now
    case-independent.
    - A bug in ARHandle initialisation which affected Windows debug builds has been
    corrected.


    Changes in version 5.0 (2013-09-06).
    ------------------------------------
    New features:
    - New format for the NFT datasets (.iset, .fset and .fset2). API is
    substantially similar, with a few necessary changes documented at
    http://www.artoolworks.com/support/library/ARToolKit_upgrade_guide#
    Upgrading_to_ARToolKit_v5.0 . You will need to regenerate your datasets using
    genTexData.
    - OpenGL ES 2.0 support. A new library libARgsub_es2 provides the essential
    connection between ARToolKit and OpenGL ES 2.0, and includes code to manage
    shader programs, and also matrix math analogues of the OpenGL fixed-function
    matrix utilities. The matrix library is useful elsewhere and so has also been
    added to libARgsub_es and libARgsub_lite. On iOS, the EAGLView class has been
    enhanced to allow runtime selection of either an ES2 or ES1 context.
    - The native video formats on Android (NV21) and iOS (420f) are now handled
    natively in ARToolKit, resulting in substantial performance improvements both in
    video handling and tracking on these platforms.
    - ar2VideoGetImage() and arglDispImage() now support retrieving and rendering
    bi-planar format images from the camera. Performance is best with libARgsub_es2,
    but even libARgsub_es's performance with these formats is better than that of
    rendering BGRA format images due to some hand-optimised ARM NEON code.

    Enhancements:
    - The iOS video module (videoiPhone) now allows requesting of different pixel
    formats at runtime via a video configuration string option. See
    http://www.artoolworks.com/support/library/
    Configuring_video_capture_in_ARToolKit_Professional#iOS_video_input_from_camera
    .
    - The ARMarkerSquare class used on iOS and native Android now automatically
    supports specification of square barcode markers in the markers.dat file.
    - Android (Java): Matching confidence and confidence cutoff may be queried.
    - Greatly improved support for different stereo display types in the stereo
    examples (stereo and stereoOptical) and calib_optical. Use the --help
    command-line option to see the control parameters.
    - Many more of the examples now use the ARMarker* classes, which offer a simple
    standard way to specify markers via a file (markers.dat by default), including
    (on desktop): simpleOSG, nftSimple, nftBook, stereo, optical, and stereoOptical,
    all apps on iOS except ARAppES1 and ARApp, and on Android all the fully-native
    apps.
    - Several more apps now support model loading and rendering via OpenSceneGraph,
    through the VirtualEnvironment class or C-pseudoclass.
    - Command-line options have been improved amongst the utilities. Use '-h' or
    '--help' after any utility name to see a full listing of its command-line
    options.
    - Optical see-through calibration has been improved, with better on-screen help,
    and with support for calibrating stereo optical displays against a single
    camera.
    - On Android, the Eclipse project files have been improved with the addition of
    C project files for the mixed-native and native examples. The CDT Eclipse plugin
    is required. See http://tools.android.com/recent/usingthendkplugin.
    - When using template matching (square picture-based markers) with mono or
    biplanar video formats, mono matching will be selected by default. Conversely
    colour matching will be used for colour formats.
    - iOS: When using the front camera, the image will be mirrored by default. This
    is achieved by new flipping support in ARView and argl. Previously, this
    flipping was achieved by mirroring the incoming video, but this caused other
    problems (e.g. NFT wouldn't track correctly). Now, tracking occurs correctly,
    and the effects on lighting of OSG models are also offset by support in libARosg
    (via VEObjectOSG class) for reversing the polygon winding when mirroring the
    video rendered scene. See example usage in ARViewController and ARView.

    Bug fixes:
    - Saving of optical parameters from calib_optical had been broken in a release
    in the 4.6 series, and this has been fixed. Optical calibrations will need to be
    recalibrated. Additionally, the optical parameter matrix stored on disk is now
    the position of the camera relative to the observer's eye, rather than the
    reverse. This makes use of optical parameters in rendering a single matrix
    multiplication. See optical/stereoOptical for new example usage.
    - Linux: The configure script now offers an option to avoid trying to build
    ARToolworks-internal-only code (i.e. libARICP and the NFT code).
    - Hundreds of other minor bug fixes.
    - iOS: Camera parameters for 16:9 video formats will now be more reliably drawn
    from 16:9 calibrations.
    - Android native apps will 'fill parent'. For the other apps using the camera
    preview, it's more complicated… a solution will be provided in a later release.
    - An issue on OS X when 2 USB cameras can't both be served simultaneously should
    now result in a graceful failure with a timeout error message rather than a hang
    inside libARvideo.

    Other changes:
    - For performance, an optimised form of the calibrated camera parameters
    (ARCparamLT) is now used internally by ARToolKit. See the examples for usage,
    and the upgrade guide for API changes. Camera parameters format on disk is
    identical, although it is also possible to save and load the optimised form on
    disk.
    - iOS/Android: The OpenGL ES state cache (glStateCache) implemented by ARToolKit
    has been updated. If you are using OpenGL commands in your app, it is advisable
    to examine the list of functions whose state is handled in the cache, so that
    you are able to switch your usage to the cache and achieve correct and optimal
    rendering. Multitexturing support has been added to the ES1 cache.
    - The optical see-through example is now named "optical" rather than
    simpleLiteOptical. The new stereo optical example is named stereoOptical.
    - Android: ARNativeExample is now named just ARNative.
    - Android: native apps using ARToolKitWrapper don't need to link against
    libjpeg, since it's now linked into the wrapper itself.
    - iOS: Objective C private instance variables in classes such as
    ARViewController, ARView and VirtualEnvironment are now listed in the
    @implementation block, consistent with modern Objective C runtime style.
    - Marker pose filtering is now available to all examples using the ARMarker*
    classes. The simpleOSGFilter desktop example has been removed.
    - Continuous pose estimation, which was previously used by default has now been
    made a user-enabled option (i.e. it is off by default). This will result in
    increased "jitter" of marker poses, but should alleviate the problem where badly
    calibrated cameras would produce bizzare "inverted" poses. It is still
    recommended to use good camera calibration data, and re-enabled continuous pose
    estimation in your code.


    Changes in version 4.6.9 (2013-04-09).
    --------------------------------------
    New features:
    - ARToolKit for Android: Added a user-visible camera preferences screen to the
    examples. The preferences screen is automatically added to any applications
    based on ARBaseLib's ARActivity class. See
    http://www.artoolworks.com/support/library/
    ARToolKit_for_Android_Camera_Preferences for more information.

    Bug fixes:
    - Fixed an initialisation error introduced in 4.6.6 which affected
    auto-thresholding modes (not enabled by default).
    - Android ARMovie example: fixed issue with playback not resuming when activity
    is paused and resumed.


    Changes in version 4.6.8 (2013-03-27).
    --------------------------------------
    New features:
    - ARToolKit for Android now includes an example of playback of a video file on a
    marker surface. The example is NDK (native)-based and is named ARMovie. Movie
    playback is only supported by Android OS v4.0 ("Ice Cream Sandwich") and later
    (Android API level 14), and support varies in quality and reliability from
    device to device. It is highly recommended that you provide alternate playback
    mechanisms for devices where playback in the AR environment cannot proceed, e.g.
    full screen playback.

    Enhancements:
    - On iOS and Android examples which load markers from a configuration file (iOS:
    ARApp2, ARAppMovie, ARAppOSG; Android: ARNativeOSG), the tracking will now
    automatically be set to match the types of square markers (template (pictorial)
    vs. matrix (barcode)) used in the configuration file. It is not recommended that
    template and matrix markers are mixed in the same application, as this lowers
    the tracking reliability of both types.

    Bug fixes:
    - Android: A reliable fix has been found for the long-standing issue on some
    devices where after an app is exited and relaunched, the camera preview surface
    appears above the augmented surface. The fix adds a call to
    GLSurfaceView.setZOrderMediaOverlay(true), and then adds the camera preview to
    the window before the GLSurfaceView. Java-based apps will automatically inherit
    the fix (via ARBaseLib). Code based on the native examples should be updated
    with the updated method in the example's Activity.onStart() method.
    - Android: Improvements to the startup and shutdown of the example Activity
    classes mean that the previous requirement for the ARActivity to have
    noHistory:true set in its manifest has been removed.
    - Android: The DEBUG preprocessor macro is now defined in the native code
    modules when building in debug mode. (Previously, only NDEBUG was available, for
    release mode builds).


    Changes in version 4.6.7 (2013-03-05).
    --------------------------------------
    Enhancements:
    - Extra functionality for handling OSG objects with animations has been added to
    arOSG.

    Bug fixes:
    - Android: fixed a bug introduced in 4.6.6 which affected optimised code running
    on devices with an ARMv7 CPU without NEON (including Nvidia Tegra 2-based
    devices).
    - Fixed a rendering bug in EdenSurfacesDraw (added in 4.6.6).


    Changes in version 4.6.6 (2013-02-11).
    --------------------------------------
    New features:
    - A new Android native example demonstrated loading of square markers and
    rendereing with OSG.

    Enhancements:
    - Portions of the utility library libEden's "Surfaces" interface for texture
    handling has been reworked. A new function EdenSurfacesDraw provides a
    convenient method for drawing a texture in an OpenGL scene.
    - For the iOS NFT examples, loading/unloading of the .fset data has been moved
    into the ARMarkerNFT class. For the purposes of page numbering, a weak reference
    to the data is still held in the ARViewController class. With this change, it is
    now possible to get the width and height of an NFT surface by querying
    marker_width and marker_height. Previously this was possible only for square
    markers.
    - iOS/Android (ARM) improved performance of image processing for
    auto-thresholding and NFT. For native Android applications, the Android
    "cpufeatures" static library must be linked along with ARToolKit's native
    libraries.
    - iOS: Improvements to -capturePhoto method and enabled options for optimised
    flipping/rotating of incoming video. Also enabled "photo", cif (352x288) and
    1080p (1920x1080) video resolutions.


    Changes in version 4.6.5 (2013-01-14).
    --------------------------------------
    New features:
    - In the OSG-based examples on the desktop platforms (simpleOSG and
    simpleOSGFilter) support is now included for loading common image formats as
    models. Additionally, a transparency hint can be supplied. This allows for (for
    example) transparent .png files to be displayed on markers. An example file has
    been included in these examples, displaying the ARToolworks logo on the
    "sample2" pattern.


    Changes in version 4.6.4 (2012-12-21).
    --------------------------------------


    New features:
    - Android: Asset handling on Android has been overhauled. Previously, assets
    required by the native code were unpacked in the Activity's onCreate() method to
    a folder named "AR" in the external storage, resulting in wasted launch time,
    unreclaimed storage space if the app was uninstalled, and potentially, asset
    conflicts. Now, assets are unpacked in an Application subclass to the
    application's cache on the internal storage. On subsequent launches, the assets
    are used from cache, saving time. Also, if space on the device is short, Android
    can clear this cache automatically, or the user manually. Finally, if the app is
    uninstalled, this space is reclaimed. One rule needs to be observed: if the
    application's assets are changed, the "VersionCode" field (an integer) in the
    application's AndroidManifest.xml MUST be changed (usually incremented).

    Enhancements:
    - iOS: In iOS video module, added tokens for iPad (4th generation) and iPad
    mini. Also, renamed iPad (March 2012) to iPad (3rd generation). Both new iPads
    use the same camera calibration as the iPad 3.
    - iOS: In CameraVideo, added "flipH" property, and "-capturePhoto" method.
    - Android: Transfer of video frames from Java to native now always uses
    JNI_ABORT in the operation. Previously, this behaviour was seen by default on
    some devices, while others were engaging in expensive reverse copies (causing a
    lot of garbage collector activity). This is a performance enhancement.

    Bug fixes:
    - iOS: Corrected an issue under iOS 6 where the ARViewController was getting
    unwanted autorotations as the device was rotated. See
    http://www.artoolworks.com/support/library/
    Updating_an_AR_application_with_the_latest_ARToolKit_for_iOS_example_code for
    more info.
    - Added an ARLOGperror() macro and used it where required. This should improve
    debug output on Android.
    - iOS: The obsolete "screenshot" method has been removed from ARViewController.
    The recommended means of taking a snapshot of the ARView is -snapshot and
    related methods in ARApp's ARViewController.m.

    Other changes:
    - Android: Changed ARToolKit.java's initialiseNative method to expect path to
    resources directory, and changed ARActivity.java to supply the cache directory
    as working directory. Updated Java-based examples to match. However, the native
    (NDK-based) examples will infer the path to the cache directory based on the
    package name. This will be improved in a later release.
    - iOS: In the NFT examples, trackingSub has been made identical to the version
    on the desktop-OS examples.


    Changes in version 4.6.3 (2012-12-06).
    --------------------------------------
    New features:
    - The OpenSceneGraph (OSG) model loader and renderer is now supported in
    ARToolKit for Android. At present, support is limited to NDK-based applications.
    A new Android example nftBook provides a full demonstration of OSG rendering.
    The Android.mk file shows how to link correctly. Note that prior to linking, the
    OSG libraries are extremely large, but will shrink considerably after symbol and
    dead code stripping during linking. OSG version 3.1.4 is supplied.

    Enhancements:
    - Android: Updated to build with Android NDK r8c, and added support for x86 and
    mips architectures. Updated to OpenCV 2.4.3. These changes require dropping
    support for Android 2.1 (API level 7). Android 2.2 (API level 8) is now the
    minimum supported version.
    - Video encoded with an alpha channel is now supported by the QuickTime video
    input module. (Available on 32-bit Windows and Mac OS X only, can be selected by
    using "-device=QUICKTIME" for video config.) The calling application must
    enabled blending on the OpenGL texture for video with an alpha channel to render
    correctly. (Typically: glBlendFunc(GL_SRC_ALPHA, GL_ONE_MINUS_SRC_ALPHA);
    glEnable(GL_BLEND);)

    Bug fixes:
    - A bug in mk_patt which prevented pattern-based square markers with
    non-standard border sizes being correctly saved has been fixed. Markers
    generated with non-standard border sizes should be regenerated.
    - A correction to a macro in video2.c now allows the new VideoImage module to
    open correctly on non-Mac OS X platforms.

    Other changes:
    - The Android ARNativeNFT example has been renamed to nftSimple, for consistency
    with other supported ARToolKit platforms.


    Changes in version 4.6.2 (2012-10-29).
    --------------------------------------
    Enhancements:
    - A new video input module "VideoImage" allows input from one or more JPEG
    images. This module is enabled by default on Windows, Linux and Mac OS X, and
    can also be enabled on iOS with a single change to include/AR/config.h.
    - iOS: Add a notification and properties to ARView for touch events.
    - iOS: In ARAppOSG's VEObjectOSG, listen for touches and correctly work out when
    they intersect the models.

    Bug fixes:
    - Fixed a serious issue with filtering. On all platforms using the ARMarker
    structure or class, filters were not being automatically reset after loss of
    tracking, resulting in some circumstances in the filtered position placing the
    object well outside the field of view. This bug fix should solve one source of
    the "disappearing object" bug in ARToolKit for Unity.
    - Created a user-editable constant "PAGES_MAX" for the NFT examples (nftSimple &
    nftBook on Mac OS X, Windows and Linux; ARAppNFT & ARAppNFTOSG on iOS,
    ARNativeNFT on Android) which sets the maximum number of NFT pages that may be
    specified in the markers.dat file.
    - iOS: Corrected a bug in ARView in touch-coord projection when the OpenGL
    content was drawn rotated with the device.
    - iOS: Fixed bug where some of the iPhone .nib files were missing the
    "fullscreen" property on their UIWindow instances, resulting in loss of touch
    events along the bottom of the screen.
    - iOS: Added clearing of stencil buffer (when present, which by default was
    never), in ARView.


    Changes in version 4.6.1 (2012-10-03).
    --------------------------------------
    Enhancements:
    - Support for iPhone 5 and iPod touch 5th Generation screen size and cameras.
    - Support for Apple's iOS 6 has been added. Support for iOS 6.0 requires use of
    Xcode 4.5, and this has a number of consequences; binaries are now built as
    armv7 + armv7s. armv6 is no longer supported, meaning that the minimum
    deployment target is now iOS 4.3, and the iPhone 3G can no longer be supported
    (the oldest supported model is now the iPhone 3GS). The project files have been
    updated to reflect this change. Users who still wish to support iPhone 3G can
    continue to use ARToolKit for iOS 4.6.0 (release 11) with Xcode 4.4.x.'
    - The bundled OpenSceneGraph libraries have been updated to v3.1.3 on iOS.

    Bug fixes:
    - A problem with texture loading when using Wavefront .obj models in the Android
    examples has been fixed. Now, a new function glmReadOBJ2 delays loading and
    submission of the textures until the model is ready to be drawn. Previously,
    texture loading was performed when the model was loaded, and typically no OpenGL
    context would be valid at that point.
    - On Android, debug output now goes to the Android logging facility, meaning
    that debug output from native ARToolKit should now be visible in Logcat (with
    the log tag "libar").
    - calib_camera now accepts file names with spaces when saving the calibrated
    parameters.
    - Extraneous header inclusions removed from simpleMovie.c.


    Changes in version 4.6.0 (2012-08-31).
    --------------------------------------
    New features:
    - NFT tracking is now included in all ARToolKit releases on all platforms.
    - Two new examples NFT-based for the desktop platforms: nftSimple, and nftBook.
    These display simple and advanced rendering on NFT surfaces. The formats used in
    the markers.dat and objects.dat file match those found in the ARToolKit for iOS
    and Android NFT examples.
    - NFT dataset creation utilities with the same improved ease of use and
    functionality as found on the mobile platforms are now provided for the desktop
    platforms. This means NFT datasets can be shared seamlessly between applications
    on mobile and desktop. The genTexData utility replaces the genImageSet,
    genFeatureMap, genFeatureSet and makeKpmTemplate utilities. The dispFeatureSet
    replaces the dispFeatureMap and checkKpmTemplate utilities.

    Enhancements:
    - The checkid utility has had some minor improvements in command-line handling
    and the types of information displayed. Please see its help page.
    - If opening movie files as video streams (via the QuickTime video module on Mac
    OS X or Windows), note that only URLs are now accepted. To construct a "file://"
    URI for a local file, a new convenience function arUtilGetFileURI has been added
    to libAR. The simpleMovie example shows the new simplified usage.
    - Pixel format information is now handled more consistently throughout the SDK,
    with AR_PIXEL_FORMAT used everywhere and AR_PIXEL_FORMAT_INVALID used to signal
    an invalid or unhandled format.
    - The calib_camera, calib_stereo and check_id applications have been improved
    and enhanced with better handling of command-line options. Run these utilities
    with the -h or --help option to see a summary of available options.
    - The winDF video module for interfacing with the Point Grey FlyCapture SDK
    (Windows-only) has been enhanced with some runtime configurable options. See
    http://www.artoolworks.com/support/library/
    Configuring_video_capture_in_ARToolKit_Professional#
    AR_VIDEO_DEVICE_WINDOWS_DRAGONFLY for details.
    - The OSG-based projects now build for 32- and 64-bit on Mac OS X, provided OSG
    v3.1.3 or later is used. See http://www.artoolworks.com/dist/openscenegraph for
    an installer for OSG for Mac OS X.
    - A full OSG release is now bundled with ARToolKit for Windows.

    Bug fixes:
    - When using calib_camera or calib_stereo, camera frame sizes bigger than the
    screen were being cropped. This has been corrected by retaining the full frame
    tracking but scaling the drawn frame onscreen.
    - A buffer overrun error in arUtilGetFileURI has been fixed.

    Other changes:
    - For examples using gsub_lite, initialisation via arglSetup has changed. Now,
    an ARParam structure (holding the camera parameters) and pixel format are passed
    in instead of an ARHandle. If debug display mode functionality is required (for
    non-NFT tracking), this is now initialised separately in a new call.
      For example, in your non-NFT applications, change:
          gArglSettings = arglSetupForCurrentContext(gARHandle);
      to:
          gArglSettings = arglSetupForCurrentContext(&(gCparamLT->param),
    arVideoGetPixelFormat());
          arglSetupDebugMode(gArglSettings, gARHandle);
      See main() in simpleLite.c for example usage.
    - Support for Microsoft Visual Studio 2008 SP1 has been dropped.


    Changes in version 4.5.11 (2012-07-18).
    ---------------------------------------
    Enhancements:
    - Handling of pre-supplied iOS camera calibration data has been improved. More
    information can be found in the iOS release notes.
    - The artoolkit-setenv script (which sets the ARTOOLKIT_4_ROOT environment
    variable on Mac OS X and Linux) should now function correctly on Mac OS X again.
    - Add Android-compatibility to arUtilChangeToResourcesDirectory(). The current
    "best" Android behaviour is to change to the root of the external storage
    (typically /mnt/sdcard or /sdcard (pre-Android OS 3.0)).

    Bug fixes:
    - The default filter cutoff (5 Hz) was a bit too low. The default is now 15Hz.
    This can of course be changed by the user.
    - Fixed a packaging error on Windows installers that left out some files
    required by the simpleOSG and simpleOSGFilter examples.


    Changes in version 4.5.10 (2012-07-04).
    ---------------------------------------
    Enhancements
    - Improved the Windows configure script.


    Changes in version 4.5.9 (2012-04-17).
    --------------------------------------
    Bug fixes:
    - iOS: Fixed bug introduced in version 4.5.8 whereby incorrect tear-down of the
    camera connection could under some circumstances lead to a crash.
    - iOS: Corrected Objective C object disposal in case of initialisation failure
    in VirtualEnvironment and VEObject* classes.

    Other changes:
    - iOS/Android: Changed marker handling to search for maximum of 30 markers per
    frame, and maximum of 25 picture (template) markers. (Limits on other platforms
    are 60 and 50 respectively.)
    - Android: the ARSimpleBarcode example has been renamed ARNativeBarcode, to
    better reflect its structure.
    - iOS: Users of the MovieVideo class can now listen for the NSNotification
    MovieVideoPlayBackEndedNotification to be notified of the end of playback of a
    movie file.
    - iOS: Improved handling of errors during movie loading in MovieVideo and
    VEObjectMovie classes.
    - iOS: Added correct compile-time flag for disabling Thumb code-generation when
    using LLVM compiler.


    Changes in version 4.5.8 (2012-03-28).
    --------------------------------------
    Enhancements:
    - Added support for the iPad (March 2012) to the iOS release. Also improved
    support for future iOS-based devices.

    Bug fixes:
    - Fixed bug in an OSG header encountered when using Xcode 4.3.x.

    Other changes:
    - Modification in behaviour of arPattLoadFromBuffer to allow use of const string
    parameter.


    Changes in version 4.5.7 (2012-02-14).
    --------------------------------------
    Enhancements:
    - Added arUtilChangeToResourcesDirectory function to allow one-line control of
    application resource path search behaviour.

    Bug fixes:
    - Mac OS X: Fixes for calling into the QuickTime7 video module from
    non-Objective C applications.

    Other changes:
    - Support for Microsoft Visual Studio 2005 SP1 (vs80sp1) has been dropped.
    - SGI Irix has not been supported for some time, and has now been dropped.


    Changes in version 4.5.6 (2011-10-18).
    --------------------------------------
    Enhancements:
    - iOS: The iPhone 4S is now supported; a full set of camera calibration files is
    included.

    Bug fixes:
    - iOS: Some memory leaks in marker and object file loading have been fixed.


    Changes in version 4.5.5 (2011-08-09).
    --------------------------------------
    Enhancements:
    - Extended controls and modes for ARvideo 1394dc.
    - Provides support for ARToolKit NFT v3.50.0.
    - Added matrix scaling functions to EdenMath.
    - arOSG now supports the concept of a "local transform". This is applied after
    the object's normal pose transform. Typically the pose transform is used to set
    the modelview matrix for the object, so the local transform allows translation,
    rotation, scaling or any combination

    Bug fixes:
    - Changed default threshold mode back to MANUAL. Auto modes have proven
    unreliable and will be improved in a future release.


    Changes in version 4.5.4 (2011-05-30).
    --------------------------------------
    Enhancements:
    - Extended controls and modes for ARvideo 1394dc.
    - Provides support for ARToolKit NFT v3.50.0.


    Changes in version 4.5.3 (2011-05-05).
    --------------------------------------
    New features:
    - An online 2D barcode marker generator is available now at
    http://www.artoolworks.com/support/app/marker.php.

    Enhancements:
    - The 4x4 barcode marker set, and two new error-checking and correction codes
    can now be selected at runtime.
    - check_id now has command-line switches to control parameters of the markers
    being used.

    Bug fixes:
    - A bug that prevented use of variable-border size markers has been fixed.


    Changes in version 4.5.2 (2011-04-20).
    --------------------------------------
    Enhancements:
    - arOSG now allows lighting to be turned on or off per model in the model .dat
    files. Also, it now allows for setting of viewpoints with the origin left or
    below (0,0).
    - A programmatic interface to the QuickTime movie interface is now exposed as
    <AR/sys/videoQuickTimeMovie.h>. The QuickTime "movie" object can be retrieved
    via a new function call ar2VideoGetMovieQuickTime().
    - A number of iOS-specific code improvements are documented in the iOS release
    notes.

    Bug fixes:
    - ar2VideoGetParams now correctly accepts a pointer to a string for the returned
    string parameter.
    - arOSG now turns off all ambient lighting.
    - The examples now create a window the same size as the incoming camera frame.
    Previously, a hard-coded window size was used.
    - A number of iOS-specific bug fixes are documented in the iOS release notes.


    Changes in version 4.5.1 (2011-03-18).
    --------------------------------------
    Enhancements:
    - The arOSG library has added support for intersection queries, plus
    enabling/disabling lighting. Also, much more state information can now be
    queried.

    Bug fixes:
    - Mac OS X: An error which occured when closing the video stream has been
    corrected.
    - Mac OS X: The QuickTime7 video module will now default to supplying 32-bit
    BGRA pixels on Intel architectures and 32-bit ARGB pixels on ppc architectures.
    This can be overridden (e.g. to supply 2vuy or yuvs-format pixels) using the
    video config string.


    Changes in version 4.5.0 (2011-01-24).
    --------------------------------------
    New features:
    - arFilterTransMat functions to provide pose-estimate filtering.
    - Support for Microsoft Visual Studio 2010.
    - mk_patt can now train markers with non-standard border widths. The command
    line switch "-border=n" (n between 0 and 0.5 (not inclusive)) specifies the
    desired border width as a proportion of the marker width. The portion of the
    marker which will be used as the pattern is now indicated by mk_patt by
    outlining in blue. Note that in order to use markers with non-standard border
    widths, the border width must be specified in the application by using the
    arSetBorderSize() function (see reference documentation for more information.)


    Changes in version 4.5.0d3 (2011-01-06).
    ----------------------------------------
    New features:
    - New QuickTime7 video input module for Mac, using the new QTKit Capture APIs.
    It is now the default video input module on the Mac. This new module offers a
    dramatic improvement in capture speed from high-definition video sources. If
    desired, ARToolKit can now be built with Mac OS X 10.6 the minimum version
    supported.
    - New example simpleMovie, demonstrating use of the QuickTime video input module
    to show a video file on a marker.
    - New utility, check_id, which allows low-level debugging of multi-marker
    tracking, particularly barcode marker tracking. See
    http://www.artoolworks.com/support/library/Debugging_marker_recognition_problems
    for a tutorial.

    Other changes:
    - Support for Microsoft Visual Studio .NET 2003, and OpenVRML 0.14.3 have been
    dropped.


    Changes in version 4.5.0d2 (2010-11-22).
    ----------------------------------------
    New features:
    - Variable marker border width. See documentation for
    arSetBorderSize()/arGetBorderSize().
    - Error detection and correction codes with 3x3 matrix markers. Two modes are
    available, one using parity, and allowing for detection of single-bit errors
    with up to 32 markers, and one using a Hamming (6,3) code, allowing for
    detection of up to 3 bit errors and correction of up to 2 bit errors with up to
    8 markers. Marker patterns for these modes can be found in the doc/patterns
    directory.
    - For identified square regions, which ultimately are not judged by ARToolKit to
    be known patterns, support is now included for discovering which stage of marker
    matching cutoff occured. See the documentation for the cutoffPhase member of the
    ARMarkerInfo structure.

    Enhancements:
    - On Mac OS X, adaptive thresholding makes use of the Accelerate framework for
    improved performance.

    Changes in version 4.5.0d1 (2010-10-05).
    ----------------------------------------
    New features:
    - Adaptive thresholding. This algorithm adjusts the threshold intra-frame, and
    thus should help ARToolKit find markers when lighting condtions are non-uniform
    across a frame. Adaptive thresholding requires a fast computer, and is not
    enabled by default. The processing time taken is proportional to the number of
    pixels in the image; using an 800x600 image size or smaller is recommended. It
    can be enabled by calling arSetLabelingThreshMode(arHandle,
    AR_LABELING_THRESH_MODE_AUTO_ADAPTIVE); Manually changing the threshold will
    disable adaptive thresholding. The kernel size
    (AR_LABELING_THRESH_ADAPTIVE_KERNEL_SIZE_DEFAULT) must be an odd number, and can
    be changed at compile-time. Larger values will provide better thresholding but
    require a faster CPU.


    Changes in version 4.4.3 (2010-08-20).
    --------------------------------------
    New features:
    - Added arVideoSaveImageJPEG() funtion, which saves video frame to a jpeg file.
    - Added a new auto threshold algorithm, based on Otsu's method, and changed this
    to the default method. Otsu's method typically selects a better threshold than
    the median, particularly when one or more markers are close to the camera.

    Enhancements:
    - Add new config token AR_ENABLE_MINIMIZE_MEMORY_FOOTPRINT. Enabled by default
    on iPhone, it removes support for the debug image, and saves several hundred KB
    of memory.

    Bug fixes:
    - Extraneous debug output from the pose estimator (ICP) now only present in
    debug builds, and goes to stderr.
    - Fix for small memory leak in arVideo.


    Changes in version 4.4.2 (this release) (2010-03-16).
    -----------------------------------------------------
    New features:
    - Auto-thresholding. ARToolKit will now by default automatically adjust the
    binarization threshold to the median image brightness. The brightness is
    measured using a full-image histogram, which runs by default every 8 frames.
    Note that if your ARToolKit application manually sets the threshold at any time
    (including during initialization) the auto-thresholding will be disabled.
    - New OpenSceneGraph-based rendering library, arOSG. arOSG is intended to
    provide access to the modern plugin-based scene graph OpenSceneGraph, and its
    attendant model formats and graphical capabilities. An example and full API
    documentation is included.

    Enhancements:
    - Windows binaries of ARToolKit are now supplied with win64-x64 versions of
    ARICP. win32-i386 versions now also build to subfolder of lib.
    - Update Windows DragonFly video module for latest FlyCapture SDK release
    (changes submitted by Henry Chu).
    - Reduced contrast required to identify barcode patterns (changed
    AR_PATT_CONTRAST_THRESH2 in arConfig.h to 15.0). This should enhance detection
    of barcode patterns.

    Bug fixes:
    - Fixup of handling of path separators on Win32 in utility functions to support
    osgART Professional Editon v1.1.3 ARToolKit4 and ARToolKit4NFT tracker plugins.

    s
    Changes in version 4.4.1 (2009-09-15).
    --------------------------------------
    Bug fixes:
    - Moved some symbols from libARvideo to libAR to avoid requirement to co-link.


    Changes in version 4.4.0 (2009-07-16).
    --------------------------------------
    New features:
    - Add line matching to pose estimator.
    - ARG: added "flipmode" for horizontal and vertical flipping.

    Enhancements:
    - Mac can also now use video1394dc.
    - New version of video1394dc, with headers and source, and configuration items.
    - Add draw square to ARG.
    - Add video pixel format name utility function.

    Bug fixes:
    - AR_AREA_MAX changed from 1e5 to 1e6. Tracking will now function better with HD
    images when marker is close to the camera.
    - Bug fixes in video1394dc.
    - Robust ppose estimator now makes better probability estimates.
    - Removal of 'static' qualifiers in multi lib.
    - Remove erroneous default video config in mk_patt for Windows DirectShow video.
    - Syntax error fixed in arViewerCapi.cpp.
    - Fix bug in videoQuickTime when UVC driver incorrectly reports frame timing.
    - Correct potential error in marker detection loop in examples.
    - Fix bug whereby request for a non-default pixel format was ignored by
    gsub_lite.
    - Change internal lib linkage in Xcode.
    - Removed some debug output from ARICP library.


    Changes in version 4.3.4 (2008-11-11).
    --------------------------------------
    Enhancements:
    - Add support for 3 packed pixel formats (RGB565, RGBA5551 and RGBA4444).
    - Addition of asynchronous fetching of video frames. New function
    ar2VideoGetImageAsync. At present, implemented only in dummy video.
    - Support for requesting power-of-2 sized buffers (via config string
    "-bufferpow2") from dummy video lib.
    - Replaced all double-precision floating point declarations with a macro which
    can be redefined to single-precision floating point as an optimisation.
    - Add 4x3 and 8x6 multi patterns and PDFs and Letter-size multi PDF.
    - Change multi-marker loading to allow backwards compatibility with config files
    from ARToolKit v2.x.

    Bug fixes:
    - Some gstreamer fixes incorporated, including correct pre-rolling with some
    additional source types, correction of default video config, and compatibility
    with new gstreamer releases.
    - Fixes to dual-mode marker detection (two pass detection of both matrix and
    template markers). arSetPatternDetectionMode no longer incorrectly rejects
    two-pass modes as invalid.
    - Debug image alpha channel (where appropriate) is now set to opaque.
    - More headerDoc documentation added.


    Changes in version 4.3.3 (2008-02-18).
    --------------------------------------
    New features:
    - Scripts to set and unset the ARTOOLKIT_4_ROOT environment variable have been
    added for the Linux and Mac OS X platforms. See the "share" directory.
    - A script "share/artoolkit5-config" allows 3rd-party applications to query
    ARToolKit build settings on the Linux and Mac OS X platforms.

    Bug fixes:
    - ARToolKit now assumes a little-endian architecture on Linux if the
    __BIG_ENDIAN__ macro is not defined by the preprocessor.
    - Change in multi-marker pattern file format (arMultiReadConfigFile); pattern
    filenames in a multimarker config file are now relative to the config file,
    rather than the working directory.


    Changes in version 4.3.2 (2008-01-20).
    --------------------------------------
    New features:
    - A new example, multiCube, demonstrates the use of non-planar multimarker sets,
    in this case a cube. Sample PDFs for cube markers are in doc/patterns/Cubes.
    - Add VideoGStreamer (LGPL license) which uses the GStreamer library for video
    input. Copyright Hartmut Seichter and ARToolworks, Inc.

    Enhancements:
    - The environment variable ARTOOLKIT_4_CONFIG can now be used to globally set
    the video configuration to be used when none is specified in the call to
    ar(2)VideoOpen().

    Bug fixes:
    - Configuration of Makefile builds (Linux, and optionally Mac OS X) has been
    cleaned up.
    - "-device=" option can now safely be passed to video input modules which don't
    use "-option" syntax.
    - gsub_lite is now correctly built in Makefile builds.


    Changes in version 4.3.1 (2008-01-08).
    --------------------------------------
    Other changes:
    - Update Xcode project for Xcode 3.0 compatibility.
    - Add arVideoUtilGetPixelFormat to libARvideo (duplicate of libAR's
    arUtilGetPixelFormat) to allow independent linkage.


    Changes in version 4.3 (2007-10-31).
    ------------------------------------
    New features:
    - Hirokazu Kato has rewritten his original fast pose estimator a modern
    algorithm. The new pose estimator offers comparable accuraccy, with much
    improved speed.
    - A robust pose estimator has been added. See the documentation for functions
    arGetTransMatRobust() and arGetTransMatStereoRobust(). These functions are also
    available under multi-marker tracking.
    - Examples for multi-marker tracking and stereo tracking added.
    - Video input via QuickTime from file and streaming video sources has been added
    on Mac OS X and Windows. Full documentation is available in the ARToolworks
    support library.
    - A set of utilities for Linux 1394dc video have been added: whitebalance,
    checkimage, listcamera.

    Enhancements:
    - Camera calibration is now performed using the OpenCV library and is greatly
    simplified. A new version 4 of the camera calibration parameters is now saved.
    Camera calibration files generated with the earlier (versions 1 through 3) of
    the camera calibration utility may still be used. The old camera calibration
    utility is available as calib_camera_old-v3.
    - Multi-marker tracking is now available in two modes, template (pictorial
    markers) and matrix (2D-barcode markers). These modes can be used exclusively or
    together in a two-pass arrangement.
    - Some convenience functions added to gsub library: argGetScreenSize(),
    argSetWindowSize().
    - Video parameters under the Linux 1394dc video library can now be saved and
    restored.
    - ARvrml, the VRML renderer, now supports openvrml-0.16.6 on all platforms, and
    builds as a DLL on Windows to ease Building of programs that use ARvrml.

    Bug fixes:
    - arUtilSleep() now correctly operates in milliseconds on Unix-based systems.

    Other changes:
    - Minor changes in the parameters to some functions: please check the
    documentation for more information: arGetDebugMode(), arGetLabelingMode(),
    arGetLabelingThresh(), arGetImageProcMode(), arGetPattDetectionMode(),
    arGetMarkerExtractionMode(), arGetTransMat(), arGetTransMatStereo(),
    argGenImageTexture().
    - The following functions have been removed: arGetTransMatSub(),
    arGetTransMatSubStereo(), arModifyMatrix(), arModifyMatrixStereo(),
    arGetAngle(), arGetRot(), arGetNewMatrix(), arGetInitRot().


    Known issues in this release.
    -----------------------------
    - The Mac video library does not yet use the new QuickTime 7 video pipeline.
    - SGI video input is missing.


    Changes in version 4.1.3 (2007-05-12).
    --------------------------------------
    - Addition of routines to load and save optical calibration sets, updated
    calib_optical, and simpleLiteOptical example.


    Changes in version 4.1.2 (2007-04-24).
    --------------------------------------
    - Addition of calib_optical tool for calibration of optical see-through
    camera-display combinations.


    Changes in version 4.1.1 (2007-04-03).
    -----------------------------------------------------
    - Major modification to accommodate changing distortion function version at
    runtime. Several function prototypes have changed.
    - Lots of new headerDoc documentation in code.
    - Began maintaining ChangeLog inside release archives.

    --
    EOF