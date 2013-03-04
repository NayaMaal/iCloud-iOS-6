Provisioning profiles must be enabled for iCloud in the iOS Provisioning Portal. To enable a provisioning profile for iCloud, navigate to the App ID section of the iOS Provisioning Portal and configure your App ID for iCloud. After enabling the App ID for iCloud, regenerate your provisioning profiles to enable them for iCloud.

The setSortDescriptors: method of NSMetadataQuery is not supported.

In iOS 6, files that are protected via Data Protection cannot be used with iCloud Storage APIs.

Filenames are case-insensitive in OS X but case-sensitive in iOS. This can lead to problems when using iCloud to share files between the two platforms. On iOS, you should avoid creating files with names that differ only by case.

The behavior of coordinated read operations on iCloud Documents has changed:
In previous iOS releases, when your app performed a coordinated read operation on a file or package and the iCloud daemon noticed that there was a newer version of the item available, the coordinated read operation blocked until the newer version of the item was downloaded and written to the disk.

As of iOS 6, when you start a coordinated read operation on a file or package for which you already have a local version, the coordinated read will be granted as soon as possible, and the new version, if any, will download in the background. This call will block for downloading reasons only if you do not have a version of the file available locally.

Additionally, when the file is conflicted, the iCloud daemon will not wait until it has all the conflict losers of the file available to make the file available to your app. It will make the different versions of the conflicted file available as soon as it can. Your app can use the existing file coordination and the UIDocument callbacks to be notified when the conflict losers have been downloaded and are available.