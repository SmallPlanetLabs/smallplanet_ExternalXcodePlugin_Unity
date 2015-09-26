# UnityExternalXcodePlugin
The main goal of this plugin is to provide a system to preserves changes made to a Unity generated Xcode project post export. This is accomplished by several PostprocessBuildPlayer scripts which copy files into generated Xcode projects, as well as inserting a build script into the Xcode project which copies the latest versions of certain file out of the XCode project folder in to a safer place (one which won't get replaced by future Unity Xcode exports).

# Prerequisites
The scripts herein make one assumption; they assume that you generate your Unity builds into a folder called Builds at the project level of your Unity project.

# Install
1. Copy the contents of the Editor folder to the Assets/Editor folder of your Unity project (create the Editor folder if non exists).
2. Open Build Settings in Unity and select "Build"
3. The editor build scripts will do the following:
  * Change supported platforms to "iOS" (instead of phoneos or phonesimulator)
  * Set the base SDK to latest phone
  * Copy the project.pbxproj file to the SyncToXcode folder
  * Copy the Info.plist file to the SyncToXcode folder
  * Add a build script to all targets of the Xcode project which will copy the project.pbxproj, Info.plist, and the contents of the ExternalFiles folder on build

# Usage
General usage should be relatively painless; just remember that saves happen on Xcode builds, and restores happen on Unity builds.
