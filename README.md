MyNotes
A clean, lightweight, offline-first notes application for Android,
developed by Atyro Labs.
MyNotes is designed for quick note-taking, organized folders, rich-text
editing, checklists, themes, and safe note recovery. All note data is
stored locally on the device. The app does not require an account or an
internet connection.
> **Current release:** 1.0\
> **Application ID:** `com.mynotes.atyrolabs`\
> **Version code:** `8`
---
Table of contents
Overview
Highlights
Screenshots
App information
Features
Notes
Rich-text editor
Folders
Trash and recovery
Themes and appearance
Search, sorting and navigation
Backup and restore
Privacy and permissions
Android compatibility
Screenshots directory
Project structure
Technology stack
Architecture
Local database
Build from source
Run tests
Install the APK
Package migration
Release and versioning
Security notes for contributors
Known limitations
Contributing
License
Credits
---
Overview
MyNotes is a native Android notes app built with Kotlin and Android's
traditional View system. It aims to provide a simple and responsive
writing experience while keeping user data on the device.
The app includes:
A home screen for browsing notes
Folder-based organization
A rich-text note editor
Checklist support
Search and sorting
Light, dark, AMOLED black, system and scheduled appearance options
Custom theme/accent colours
A Trash area with restore and permanent-delete actions
Local backup and restore
MyNotes is intended to work without a cloud service. It has no sign-in,
online synchronization, advertising SDK, or analytics integration in the
supplied project.
Highlights
Offline by design: notes are stored in a local SQLite database.
No declared Android permissions: the app manifest does not
request runtime permissions.
Rich editing: supports common text formatting and checklists.
Safer deletion: notes and folders can be moved to Trash and
restored.
Live updates: note, folder and Trash views refresh after
database changes.
Theme options: includes Light, Dark, AMOLED Black, System and
Scheduled modes.
Backup and restore: export and restore notes, folders and Trash
data using an app backup file.
Small release build: the project README records an approximately
2.1 MB release APK; actual size can vary by build environment.
---
Screenshots
The screenshots below are stored in the `preview/` directory.
Home screen
![MyNotes home screen - light theme](preview/01-home-light.png)
Note editor
![MyNotes note editor](preview/02-editor-light.png)
Dark theme
![MyNotes home screen - dark theme](preview/03-home-dark.png)
Settings
![MyNotes settings](preview/04-settings-footer.png)
AMOLED black theme
![MyNotes AMOLED theme](preview/05-home-amoled.png)
Custom accent colour
![MyNotes custom accent colour](preview/06-home-purple-accent.png)
Theme preview
![MyNotes theme preview](preview/07-theme-preview.png)
Appearance settings
![MyNotes appearance settings](preview/08-settings-appearance.png)
---
App information
Item                     Value
---
App name                 MyNotes
Developer / brand        Atyro Labs
Android application ID   `com.mynotes.atyrolabs`
Namespace                `com.mynotes.atyrolabs`
Version name             `1.0`
Version code             `8`
Minimum SDK              21 (Android 5.0 Lollipop)
Compile SDK              34
Target SDK               34
Programming language     Kotlin
Build system             Gradle
Android Gradle Plugin    8.4.2
Kotlin Gradle Plugin     1.9.24
Gradle wrapper           8.7
Java compatibility       Java 17
Data storage             Local SQLite database
Network permission       Not declared
The values above are taken from the supplied Android project
configuration and project documentation.
---
Features
Notes
Create and edit notes.
Browse notes from the main screen.
Pin and unpin notes.
Assign colours to notes.
Move notes between folders or to the no-folder location.
Search notes.
Sort and browse notes.
View note previews, including checklist state.
Save changes locally.
Rich-text editor
The editor includes formatting tools for common writing tasks:
Bold
Italic
Underline
Strikethrough
Heading
Text alignment
Bullet lists
Numbered lists
Checklists
Undo and redo
Checklist items can be checked and unchecked. Checklist state is
retained when a note is saved and reopened. The editor and note preview
use the same checklist drawing component so checklist indicators remain
consistent.
Folders
Create folders.
Rename folders.
Choose folder colours.
Move notes between folders.
Move notes to the no-folder location.
Browse notes within a selected folder.
Delete folders using the Trash workflow.
Folder and note changes are reflected in the relevant screens without
requiring an app restart.
Trash and recovery
MyNotes uses a recoverable deletion workflow.
Deleted notes appear in Trash.
Deleted folders appear in Trash.
Restoring a note returns it to its folder when that folder is
available. If its folder is unavailable or still in Trash, the note
is restored to All Notes.
Restoring a deleted folder restores the notes that were moved to
Trash together with that folder.
Notes that were already individually in Trash before their folder
was deleted remain in Trash when the folder is restored.
A note or folder can be permanently deleted from Trash.
Empty Trash clears the deleted notes and folders.
Trash management settings can control retention and automatic
purging.
Important: Permanent deletion cannot be undone. Export a backup
before clearing Trash if you need to keep a copy of your data.
Themes and appearance
The Background Theme options documented in the project are:
Light
Dark
AMOLED Black
System
Scheduled
The app also provides theme/accent colour choices and theme preview
controls. AMOLED Black uses pure black surfaces where supported by the
theme implementation.
Search, sorting and navigation
The app provides note browsing, search, sorting controls, folder
navigation, bottom navigation and a dedicated Trash screen. Database
change notifications are used to refresh the data displayed by active
screens.
Backup and restore
The app includes backup and restore actions under Settings →
Application.
The backup workflow is designed to export notes, folders and Trash items
to a file and restore them on another installation. The project
documentation describes this as the migration path for users moving from
the previous application ID.
Keep backup files somewhere safe. A backup is especially important
before uninstalling the app, changing devices, or performing a factory
reset.
---
Privacy and permissions
MyNotes is designed for local, offline note storage.
Based on the supplied `AndroidManifest.xml`:
No Android permissions are declared.
The app does not declare internet access.
The app does not require an account.
The app stores notes in a local SQLite database.
Android cloud backup is disabled in the application manifest
(`allowBackup="false"` and backup content disabled).
The app's backup and restore feature is an in-app file workflow. Keep
exported backup files private because they may contain personal notes.
---
Android compatibility
The project configuration specifies:
Minimum SDK: 21 (Android 5.0)
Target SDK: 34
Compile SDK: 34
This means the app is configured to support Android 5.0 and later at the
SDK level. Device-specific behaviour can vary. The project documentation
describes testing and compatibility considerations; do not interpret the
minimum SDK setting alone as proof that every feature has been
physically tested on every Android release or device.
---
Screenshots directory
``` text
preview/
├── 01-home-light.png
├── 02-editor-light.png
├── 03-home-dark.png
├── 04-settings-footer.png
├── 05-home-amoled.png
├── 06-home-purple-accent.png
├── 07-theme-preview.png
└── 08-settings-appearance.png
```
To add a new screenshot:
Capture the app screen.
Save the image in `preview/`.
Use a clear filename.
Add it to this README using a relative Markdown image path.
---
Project structure
The main source tree is organized as follows:
``` text
MyNotes/
├── app/
│   ├── build.gradle.kts
│   ├── proguard-rules.pro
│   └── src/
│       ├── main/
│       │   ├── AndroidManifest.xml
│       │   ├── java/com/mynotes/atyrolabs/
│       │   │   ├── MyNotesApp.kt
│       │   │   ├── data/
│       │   │   │   ├── Models.kt
│       │   │   │   ├── NotesBackup.kt
│       │   │   │   ├── NotesDatabase.kt
│       │   │   │   └── NotesRepository.kt
│       │   │   ├── ui/
│       │   │   │   ├── MainActivity.kt
│       │   │   │   ├── NoteEditorActivity.kt
│       │   │   │   ├── NotesFragment.kt
│       │   │   │   ├── FoldersFragment.kt
│       │   │   │   ├── TrashFragment.kt
│       │   │   │   ├── SyncedFragment.kt
│       │   │   │   ├── SettingsFragment.kt
│       │   │   │   ├── ThemedActivity.kt
│       │   │   │   ├── adapters/
│       │   │   │   └── dialogs/
│       │   │   ├── util/
│       │   │   ├── widget/
│       │   │   └── ...
│       │   ├── res/
│       │   └── ...
│       └── test/
│           └── java/com/mynotes/atyrolabs/
├── gradle/
│   └── wrapper/
├── preview/
├── tools/
├── .gitignore
├── build.gradle.kts
├── gradle.properties
├── gradlew
├── gradlew.bat
├── settings.gradle.kts
└── README.md
```
Main source packages
---
Package / file                      Responsibility
---
`data/Models.kt`                    Data models used by the app
`data/NotesDatabase.kt`             SQLite database and schema
management
`data/NotesRepository.kt`           Note and folder operations, data
access and change notifications
`data/NotesBackup.kt`               Backup and restore operations
`ui/`                               Activities and fragments for the
app screens
`ui/adapters/`                      RecyclerView adapters and list
presentation
`ui/dialogs/`                       Dialogs and bottom-sheet style
interactions
`util/`                             Preferences, themes, colours,
typography and utility functions
`widget/`                           Rich-text editing, checklist
rendering, spans and undo support
`src/test/`                         Automated unit and UI-flow-oriented
tests
---
Technology stack
The project uses the following libraries and build tools, as declared in
Gradle:
Technology                Version
---
Kotlin Android plugin     1.9.24
Android Gradle Plugin     8.4.2
Gradle wrapper            8.7
AndroidX Core KTX         1.13.1
AppCompat                 1.7.0
Material Components       1.12.0
RecyclerView              1.3.2
ConstraintLayout          2.1.4
Activity KTX              1.9.0
Fragment KTX              1.8.0
JUnit                     4.13.2
Robolectric               4.12.2
AndroidX Test Core KTX    1.5.0
AndroidX Test Ext JUnit   1.1.5
The project uses View Binding and Java 17 source/target compatibility.
---
Architecture
The app separates data handling, user interface, shared utilities and
custom widgets.
Data layer
The data layer contains:
Data models
SQLite database management
Repository operations
Backup and restore logic
UI layer
The UI layer contains the main activity, note editor activity,
fragments, adapters and dialogs.
Utility layer
The utility layer contains app preferences, theme configuration, colour
palettes, date formatting and typography helpers.
Custom widgets
The widget package contains rich-text editing and rendering helpers,
checklist components, span encoding/decoding and undo management.
The repository publishes change notifications after committed writes so
screens can refresh their displayed notes, folders and Trash state.
---
Local database
MyNotes uses SQLite for local storage.
The project documentation identifies schema version 3. The schema
includes notes and folders, with a nullable `folders.deleted_at` field
used to represent folders in Trash. A `NULL` deletion timestamp
represents a folder that has not been deleted.
Database upgrades are designed to preserve existing data. The
Trash-related schema update is additive and idempotent according to the
project documentation.
Data handling principles
Note and folder operations are performed locally.
Related multi-row delete and restore operations use database
transactions.
A failed save should leave the editor content available for retry.
Folder deletion and restoration preserve the relationship between a
folder and the notes moved with it.
Permanent deletion is performed from Trash.
For implementation details, see `NotesDatabase.kt` and
`NotesRepository.kt`.
---
Build from source
Requirements
Install the following development tools:
Android Studio
Android SDK Platform 34
JDK 17
A compatible Android SDK Build Tools installation
The Gradle wrapper downloads Gradle 8.7 when required.
1. Clone the repository
``` bash
git clone https://github.com/YOUR-USERNAME/MyNotes.git
cd MyNotes
```
Replace `YOUR-USERNAME` with your GitHub username or organization.
2. Configure the Android SDK
Open the project in Android Studio and allow Gradle Sync to complete.
Android Studio normally configures the local SDK path automatically. If
building from a terminal, make sure the Android SDK is installed and
configured on your machine.
Do not commit `local.properties`; it contains a machine-specific SDK
path.
3. Build a debug APK
On Windows:
``` bat
gradlew.bat assembleDebug
```
On macOS or Linux:
``` bash
./gradlew assembleDebug
```
The debug APK is normally generated at:
``` text
app/build/outputs/apk/debug/app-debug.apk
```
4. Build a release APK
``` bash
./gradlew assembleRelease
```
On Windows:
``` bat
gradlew.bat assembleRelease
```
The release build configuration enables code shrinking and resource
shrinking by default. Release signing must be configured securely on
your own machine or build environment before producing a distributable
signed APK.
For low-memory build environments, the project supports disabling
minification with:
``` bash
./gradlew assembleRelease -Pminify=false
```
Do not publish private signing keys or passwords in the repository.
---
Run tests
Run the full local unit test suite with:
``` bash
./gradlew test
```
On Windows:
``` bat
gradlew.bat test
```
To run tests for the app module:
``` bash
./gradlew :app:testDebugUnitTest
```
The project includes tests covering areas such as:
Auto-save behaviour
Backup and restore
Database migrations
Repository operations
Folder creation, deletion and restoration
Trash workflows
Checklist editing, alignment and persistence
Rich-text span encoding
Theme behaviour
UI flows and state synchronization
Pagination
Database performance checks
The supplied project README reports 153 tests passing in its documented
test run. Test results can differ depending on the environment and
current source changes. Run the tests locally before making a release.
---
Install the APK
If you have built or obtained a trusted APK, install it on an Android
device.
Using ADB:
``` bash
adb install -r app/build/outputs/apk/debug/app-debug.apk
```
To install a release APK, use its actual output path.
Only install APK files from sources you trust. The repository's source
code is the recommended place to review the app before building it
yourself.
---
Package migration
The current application ID is:
``` text
com.mynotes.atyrolabs
```
The project documentation describes an earlier package ID:
``` text
com.mrhirakgamerz.mynotes
```
Android treats apps with different application IDs as separate
applications. The project includes a backup and restore workflow
intended to help users move their notes from the older application ID to
the current one.
Recommended migration process:
Open the older app.
Use its backup/export option.
Save the backup file somewhere safe.
Install the current MyNotes app.
Open Settings → Application.
Use the restore option and select the backup file.
Check that notes, folders and Trash items are present before
removing the older app.
Do not uninstall the old app until you have confirmed that the backup
has been restored successfully.
---
Release and versioning
The supplied project is labelled MyNotes 1.0, with `versionCode` 8
and `versionName` 1.0.
The project history includes earlier development labels and bug-fix
rounds. The current release keeps the visible version name at 1.0 while
retaining version code 8 for Android upgrade compatibility.
Current release notes
The 1.0 project includes the following documented fixes and behaviour:
Checklist boxes align with their text and update immediately when
tapped.
Checklist state appears in note previews.
Concurrent note saves are handled to avoid duplicate or missed
writes.
Saving into a folder that has been deleted falls back to All Notes
rather than silently failing.
Failed saves keep the editor open and preserve the text for retry.
Folder deletion uses a recoverable Trash workflow.
Restoring a folder restores the notes moved to Trash with it.
Individually deleted notes remain in Trash when their folder is
restored.
Permanent deletion is handled from Trash.
Note, folder and Trash screens refresh after committed changes.
Backup and restore support is included.
The theme system includes Light, Dark, AMOLED Black, System and
Scheduled modes.
For the full implementation history, inspect the source control history
and the project files.
---
Security notes for contributors
Before uploading this project to a public GitHub repository:
Do not commit `local.properties`.
Do not commit `.jks` or `.keystore` files.
Do not commit signing passwords, API keys, tokens or other secrets.
Keep release signing configuration outside source control, using
environment variables or secure CI secrets.
Review the complete Git history before making a repository public.
Removing a secret from the latest commit does not remove it from
earlier commits.
If a signing key or password has already been exposed, treat it as
compromised and plan an appropriate key replacement/migration
strategy before distributing future updates.
Suggested `.gitignore` additions:
``` gitignore
# Local Android SDK configuration
local.properties

# Gradle and build output
.gradle/
**/build/

# IDE and local machine files
.idea/
*.iml
.DS_Store

# Signing credentials
*.jks
*.keystore
keystore/

# Local secret configuration
secrets.properties
.env
```
Important for this supplied workspace: the uploaded ZIP contains a
keystore and the Gradle release configuration includes signing
credentials directly in the build script. Do not publish those items as
they are. Remove the keystore from the Git working tree, move signing
credentials out of the Gradle file, and review/clean Git history before
publishing. A `.gitignore` rule alone does not remove files that are
already tracked.
---
Known limitations
MyNotes is an offline, local-storage app. It does not provide cloud
synchronization between devices.
The app does not include user accounts or a web-based notes
dashboard.
The minimum SDK setting does not guarantee that every
device-specific feature has been tested on every Android device.
The supplied project configuration targets SDK 34. Re-check Android
platform requirements when preparing future Play Store releases.
Backup files must be managed by the user and stored safely.
---
Contributing
Contributions, bug reports and suggestions are welcome.
When submitting a change:
Explain the problem or feature.
Keep changes focused.
Avoid adding unnecessary dependencies.
Preserve existing note data and database migration safety.
Add or update tests for changed behaviour.
Run the relevant tests before opening a pull request.
Never include private signing credentials or personal backup files.
---
License
No license file was present in the supplied project archive.
Until a license is added, assume that all rights are reserved. If you
want others to use, modify or distribute this project, add a `LICENSE`
file with the license you choose.
---
Credits
MyNotes  
Developed under Atyro Labs.
Thank you for checking out MyNotes. If you find a bug or have an idea to
improve the app, open an issue in the repository.
