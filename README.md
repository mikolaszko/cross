# 🦀 Cross 🦀
Cross platform template for GUI development on Linux, Mac, Windows, Web, Android using egui  

## Purpose
There was no project/example of how to make a working build and run egui app on the platforms mentioned above (examples exist but separately)  
Eframe (official egui template) exists but the examples fall short and they don't provide a good way of handling Android and wasm together  
This is a ready solution, just clone the project, change the AVD in the Taskfile and you are good to go  

## Building & Testing  
Automation and Build done with [Taskfile](https://taskfile.dev/)  
Treating it as an opportunity to build a pipeline where each change to the codebase that breaks any platform can be spotted

### Native
```
cargo build & cargo run
```

### Web
Run in browser with trunk:  
```
trunk serve 
```

### Android
Android requires either a device or an emulator (for linux you might need to switch to software acceleration)

1. When running in the Android Studio you basically can coldboot emulator you have chosen that works with the NDK (for rust) and target SDK 
and the ```cargo apk run -p cross --lib``` command

2. Pure CLI setup:

```
avdmanager list # this will output the availables avds

./emulator -avd <avd> -netdelay none -netspeed full
```
One-time setup:
```
cargo install \
    --git https://github.com/parasyte/cargo-apk.git \
    --rev 282639508eeed7d73f2e1eaeea042da2716436d5 \
    cargo-apk
```

Build and run:
```
# Run on android with emulator already running
cargo apk run -p cross --lib

# Run on desktop
cargo run -p cross
```
