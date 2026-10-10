# GyroLock V17 — Rotate Expression Fix

Android camera project with gyro XYZ stabilization, autofocus on tap, zoom controls (1x/2x/4x), and torch toggle.

## Fix in V17
- Reduced FFmpeg gyro trajectory expression keyframes from 120 to 48 points.
- The previous deeply nested `if(lt(...))` expression could exceed FFmpeg expression parser limits and fail at `Parsed_rotate_0` while configuring the output pad.
- FFmpeg still evaluates the compact motion curve per frame and interpolates between the selected gyro trajectory points.
- Kept fixed rotate output dimensions (`ow=iw:oh=ih`), mirror edge fill, crop margin, and 30 FPS output.
- Kept the original recording safe; stabilization writes a separate output file.

## Build
Upload the contents of this project to the root of a GitHub repository. Run the `Build GyroLock APK` workflow from the Actions tab, then download the `GyroLock-debug-apk` artifact.

## Notes
The archive and the stabilization filter syntax were checked. This environment cannot verify a full Android build or test the APK on a physical phone. FHD and camera features depend on device support.
