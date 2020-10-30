# Repo illustrating a file lock bug in the build process of AppDynamics
## Prerequisites

- You run on Windows

## Reproduction

- Run the app from Android Studio 4.1  or gradle task `app:assembleDebug` from the command line. Observe it succeeed
- Change `Data.kt` in the `/lib` module. I.e. change "bar" to "123"
- Run the app or gradle task `app:assembleDebug`

Expected result: Builds successfully

Actual result: 
```
java.nio.file.FileSystemException 
The process cannot access the file because it is being used by another process: 
lib\build\intermediates\runtime_library_classes_jar\debug\classes.jar
```

*) Bug will also manifest itself when building from command line
