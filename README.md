# Expo Linking.getInitialURL() Intermittent Null Return

This repository demonstrates a bug where `Linking.getInitialURL()` in Expo inconsistently returns `null` when the app is launched via a deep link.  The issue is intermittent, making reliable handling of deep links difficult.

## Bug Description
The `Linking.getInitialURL()` method, used to retrieve the initial URL that launched the app, sometimes returns `null` even when a valid URL is used to open the app. This behavior is inconsistent and unreliable.

## Reproduction
1. Clone this repository.
2. Run the app in Expo Go or on a device.
3. Open the app through a deep link (as described in the `bug.js` file).
4. Observe the console output – you may see `null` returned even when the deep link was successfully used to launch the application.

## Solution
The solution, implemented in `bugSolution.js`, involves using `Linking.addEventListener` to listen for URL changes and checking `getInitialURL` in combination with the event listener.  This combination handles cases where `getInitialURL` might return `null` immediately after app launch and more consistently retrieves the deep link URL.