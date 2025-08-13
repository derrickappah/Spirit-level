# All-in-One Level Tool

## Overview

This is a simple, self-contained web-based level tool built with HTML, CSS (via Tailwind), and JavaScript. It uses your device's orientation sensors (gyroscope/accelerometer) to simulate three types of levels:

- **Bullseye Level**: A 2D circular level where a ball moves based on tilt in both axes.
- **Horizontal Level**: A bubble level for left-right tilt.
- **Vertical Level**: A bubble level for front-back tilt.

The tool includes smoothing for fluid motion, visual/audio feedback when level, adjustable smoothing, fullscreen mode, and error handling for device compatibility.

It's designed for mobile browsers (e.g., Chrome, Safari on iOS/Android) where orientation events are supported. On desktop, it won't respond to tilts but can be tested by simulating events or viewing statically.

## Features

- **Real-time Tilt Detection**: Uses `DeviceOrientationEvent` to track gamma (left-right) and beta (front-back) angles, clamped to ±45°.
- **Smoothing**: Averages the last N readings (adjustable via slider, 1-20) to reduce jitter.
- **Level Feedback**:
  - Visual: Bubbles/ball turn green with a glow when within ±1° tolerance.
  - Audio: A short beep (440Hz sine wave) when entering level state.
- **Angle Displays**: Shows current angles in degrees for horizontal and vertical.
- **Fullscreen Mode**: Toggle button for immersive view on mobile.
- **Compatibility Handling**: Prompts for iOS permissions; alerts if sensors are unsupported or denied.
- **Responsive Design**: Elements scale with screen size using Tailwind classes (e.g., `w-4/5 max-w-64`).

## How to Use

1. **Save the File**: Copy the provided HTML code into a file named `index.html`.
2. **Open in Browser**: Load it on a mobile device (phone/tablet) for tilt functionality. On desktop, it displays but doesn't move.
3. **Grant Permissions**: On iOS, tap the screen to request orientation access.
4. **Tilt Your Device**:
   - Left/right: Moves horizontal bubble and bullseye ball horizontally.
   - Forward/back: Moves vertical bubble and bullseye ball vertically.
5. **Adjust Settings**:
   - Use the smoothing slider for responsiveness.
   - Click "Toggle Fullscreen" for better visibility.
6. **Check Level**: When perfectly level, elements turn green and beep.

If no movement occurs:
- Ensure your device has sensors enabled.
- Try a different browser or restart.
- On Android, it should work without extra prompts.

## Code Structure

- **HTML**: Layout for bullseye, horizontal/vertical levels, fullscreen button, and smoothing slider.
- **CSS**: Tailwind for styling (dark theme, rounded elements, shadows).
- **JavaScript**:
  - Event listeners for orientation and UI interactions.
  - Smoothing function using moving average.
  - Update logic for positioning bubbles/ball and feedback.
  - Audio via Web Audio API.
  - Permission and fullscreen handling.

## Dependencies

- **Tailwind CSS**: Loaded via CDN (`https://cdn.tailwindcss.com`).
- **Fonts**: Google Fonts (Space Grotesk, Noto Sans) via CDN.
- No other external libraries; everything is vanilla JS.

## Limitations

- **Desktop Use**: No tilt input; for testing, you could simulate events in dev tools.
- **Browser Support**: Works best on modern mobile browsers. Older devices may lack sensors.
- **Angle Range**: Limited to ±45° for practical use; extreme tilts are clamped.
- **Audio**: May require user interaction to play (browser policies).
- **No Calibration**: Assumes device sensors are accurate; no manual offset.

## Customization Ideas

- Change colors: Edit hex codes like `#3d99f5` (blue) or `#22c55e` (green).
- Adjust Tolerance: Modify `const tolerance = 1;` in JS.
- Add More Axes: Extend for alpha (compass) if needed.
- PWA Support: Add a manifest for installable app experience.

## License

MIT License. Feel free to use, modify, and distribute.

## Credits

Built iteratively with suggestions for enhancements like feedback, smoothing, and compatibility. Inspired by physical bubble levels for digital convenience.
