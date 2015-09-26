# UnityExternalXcodePlugin
The main goal of this plugin is to provide a system to preserves changes made to a Unity generated Xcode project post export. This is accomplished by several PostprocessBuildPlayer scripts which copy files into generated Xcode projects, as well as inserting a build script into the Xcode project which copies the latest versions of certain file out of the XCode project folder in to a safer place (one which won't get replaced by future Unity Xcode exports).

# Prerequisites
UnityExyernalXCodePlugin has only been tested with Unity 5 running on Mac OS X.

The scripts herein make one important assumption; they assume that you generate your Unity builds into a folder called Builds at the project level of your Unity project.  If this doesn't work for you, you can adjust this by changing the relative path for working_directory in PostprocessBuildPlayer_ExternalXcode2; it should contain the path to get from the install location to the Unity project folder.

# Install
0. Place the entire UnityExternalXcodePlugin in your Unity projects folder
1. Copy the contents of the Editor folder to the Assets/Editor folder of your Unity project (create the Editor folder if non exists).
2. Open Build Settings in Unity and select "Build". During the Xcode project creation, the UnityExternalXcodePlugin scripts will:
  * Change supported platforms to "iOS" (instead of phoneos or phonesimulator)
  * Set the base SDK to latest phone
  * Save or restore the project.pbxproj file in the SyncToXcode folder
  * Save or restore the Info.plist file in the SyncToXcode folder
  * Restore the contents of the ExternalFiles
  * Add a build script to all targets of the Xcode project which will handle saving changes to the above three files whenever the Xcode project is built.

# Usage
General usage should be relatively painless; just remember these few things:

* Saves happen when Xcode builds
* Restores happen on Unity build an XCode project
* Put all files you want saved and restored in the SyncToXcode/ExternalFiles
