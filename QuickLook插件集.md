# QuickLook Plug-ins

## Mainly from <http://www.quicklookplugins.com/>


### [textmate quicklook](https://github.com/textmate/textmate)

Preview source code files with syntax highlighting, bundled in the textmate editor.

It's a replacement of [QLColorCode](https://code.google.com/p/qlcolorcode/)


### [QuickLook Video](https://github.com/Marginal/QLVideo)

This package allows OSX Finder to display thumbnails, previews and metadata for most types of video files.

QuickLook and Spotlight on OSX 10.9 and later understand a limited number of media files - mostly only MPEG audio and video codecs within MPEG container files. This package adds support for wide range of other codecs and "non-native" media file types, including `.asf`, `.avi`, `.flv`, `.mkv`, `.rm`, `.webm`, `.wmf` etc.

**Installation**    

* Download the `.pkg` file of the [latest release](https://github.com/Marginal/QLVideo/releases/latest).
* Double-click on it.
* The Installer app will walk you through the installation process.

**Limitations**    

* To see thumbnails of video files you may need to relaunch Finder (ctrl-⌥-click on the Finder icon in the Dock and choose Relaunch) or log out and back in again.
* You may experience high CPU and disk usage for a few minutes after installation while Spotlight re-indexes all of your "non-native" audio and video files.
* The QuickLook "Preview" function displays a static snapshot of "non-native" video files.
* Interlaced content is sometimes not de-interlaced in QuickLook thumbnails and previews.
* Requires OSX 10.9 or later. Use [Perian](http://github.com/MaddTheSane/perian) for equivalent functionality under 10.8 and earlier.

**Uninstall**

* Run the Terminal app (found in Applications → Utilities).
* Copy the following and paste into the Terminal app:

`sudo rm -rf /Library/Application\ Support/QLVideo /Library/QuickLook/Video.qlgenerator /Library/Spotlight/Video.mdimporter`
 
* Press Enter.
* Type your password and press Enter.

### App Bundles

This Quick Look plug-in is a component of `SixtyFour`(an mac app). SixtyFour can be obtained at [MacUpdate](https://www.macupdate.com/app/mac/40405/sixtyfour/).

The Quick Look plug-in included within `SixtyFour` extends QuickLook’s standard functionality to display extra info: app architectures, app platform info and bundle version. It is no longer required to fire up the Terminal to get the architectures of an app or inspect the property-list file of an app to get the bundle version.

### [String File QuickLook](http://blog.timac.org/?p=933)

A simple QuickLook plugin to preview .strings files. Contrary to other QuickLook plugins to preview .strings files, this plugin can preview plain text .strings files as well as binary property list .strings files.

### [QuickLookJSON](http://www.sagtau.com/quicklookjson.html)

quick look json is a useful quick look plugin to preview JSON files. It will render files with a colorful view, and will allow to expand or compress nodes in the JSON tree.

### [Image Dimensions and File Size in QL Title Bar](https://github.com/Nyx0uf/qlImageSize)

This is a QuickLook plugin for OS X 10.8+ to display the dimensions of an image and its file size in the title bar.

### [QLStephen](http://whomwah.github.com/qlstephen/)

QLStephen is an Apple OSX QuickLook plugin that lets you view plain text files without a file extension. It is useful for reading files like:

* README
* INSTALL
* CHANGELOG
* Makefile
* Rakefile
* CapFile

### [BetterZipQL](http://macitbetter.com/BetterZip-Quick-Look-Generator/)

Preview the contents of compressed archives.

### [Suspicious Package](http://www.mothersruin.com/software/SuspiciousPackage/)

Preview the contents of a standard Apple installer package.
See what files are installed, what scripts are run, the details of any signature on the package, and more.

### [QLMarkdown](https://github.com/toland/qlmarkdown)

Preview Markdown files.
