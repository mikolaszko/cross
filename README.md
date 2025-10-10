### Cross 
Cross platform build for Linux, Mac, Windows, Web, Android and iOS

### Why?
R&D project for future contract, performance benchmarking  
Maybe I will make a template out of it?  

## Building & Testing  
Automation and Build done with [Taskfile](https://taskfile.dev/)  
Treating it as an opportunity to build a pipeline where each change to the codebase that breaks any platform can be spotted
## Manual build commands (probably gonna delete it and keep it in the configuration)
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
