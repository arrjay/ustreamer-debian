# ustreamer-debian

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](LICENSE)

TinyPilot-specific build of a uStreamer Debian package

## Updating to new uStreamer versions

When there are uStreamer releases that would benefit TinyPilot users, we need to update the TinyPilot uStreamer repos to pull in the changes and create a new Debian package. Note that we don't create Debian packages for every uStreamer change, as some uStreamer releases don't serve TinyPilot scenarios.

### Review uStreamer's commit history

Before updating the uStreamer package, review uStreamer's commit history for anything that may impact TinyPilot scenarios.

Check the [uStreamer README](https://github.com/pikvm/ustreamer?tab=readme-ov-file#%C2%B5streamer) for any compatibility changes.

If the new version of uStreamer is a new major version, try and find out why the major version number increased.

Review all commits made to uStreamer since we last cut a release for any breaking changes or feature improvements. You can do this using a GitHub comparison, e.g., [v5.43 to v6.11](https://github.com/pikvm/ustreamer/compare/v5.43...v6.11).

Check for any other obvious breaking changes by reviewing some of the major commit diffs.

#### Reduce video frame rate (MJPEG)

1. Go to System > Video settings
1. Set FPS to 5
1. Click “Apply”
1. Verify that the video refreshes slower than it did previously

#### Reduce video quality (MJPEG)

1. Go to System > Video settings
1. Set JPEG quality to 10%
1. Click “Apply”
1. Verify that the image quality looks notably worse

#### Reset video settings

1. Go to System > Video settings
1. Click “Reset to Default” next to Frame Rate
1. Click “Reset to Default” next to Quality
1. Click “Apply”
1. Verify that video quality and latency goes back to normal

#### Use H.264 compression

1. Go to System > Video settings
1. Select Streaming Mode of H.264
1. Click “Apply”
1. Verify that H.264 icon appears on the bottom left corner and that video functions

#### Verify audio plays

1. In the target system, click the speaker icon in the upper right corner
1. Adjust the volume on the target machine
1. Verify that the confirmation beeps from changing the volume play through the local machine

#### Reduce video frame rate (H.264)

1. Go to System > Video settings
1. Set FPS to 5
1. Click “Apply”
1. Verify that the video refreshes slower than it did previously

#### Reduce video quality (H.264)

1. Go to System > Video settings
1. Set Bit Rate to 0.05 Mb/s
1. Click “Apply”
1. Verify that the image quality looks notably worse
   1. The difference is subtle. You might need to open a web browser in the target system to see the difference.

#### Reset video settings

1. Go to System > Video settings
1. Click “Reset to Default” next to Frame Rate
1. Click “Reset to Default” next to Quality
1. Click “Apply”
1. Verify that video quality and latency goes back to normal

#### Change display settings

1. On the target machine, navigate to its display settings
1. Select a different resolution (e.g., 1280x720 at 60Hz)
1. Click "Apply"
1. Verify that the video resolution changes

#### Reset display settings

1. On the target machine, navigate to its display settings
1. Select the original resolution (e.g., 1920x1080 at 30Hz)
1. Click "Apply"
1. Verify that the video resolution changes back to the original settings

### Measure latency

If the manual tests pass, measure the new latency:

1. Connect TinyPilot to a device that has a display
1. Mirror display between TinyPilot and the device's other monitor
1. On the target device, visit a website that has a stopwatch with millisecond precision
1. Take a photo that captures the TinyPilot client device's screen and the mirrored display in one photo
1. Subtract the times to get the latency
1. Repeat 3-4x to get an average
