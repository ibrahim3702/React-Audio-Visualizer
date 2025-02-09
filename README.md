# React Voice Visualizer

## [Demo App](https://react-voice-visualizer.vercel.app/)

### Overview

The `react-voice-visualizer` library provides a robust and fully customizable solution for capturing, visualizing, and manipulating audio recordings in web applications. Built with React hooks and components, this library simplifies the integration of audio recording and visualization capabilities using the [Web Audio API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API).

(./public/voiceVisualizer.png)

Experience the [Demo App: Click here to explore the React Voice Visualizer](https://react-voice-visualizer.vercel.app/). Try it out and see it in action!

### Key Features:

- **Audio Recording**: Capture audio recordings effortlessly with React hooks and components.
- **Visualization**: Visualize audio data in real-time, ideal for applications like voice recognition and sound analysis.
- **Customization**: Fully customizable to fit your project's unique requirements.
- **Responsiveness**: Create audio applications that adapt seamlessly to various devices and screen sizes.

This README serves as a comprehensive guide for effectively utilizing the library's features.

## Installation

To add the React Voice Visualizer library to your project, use npm or yarn:

```bash
npm install react-voice-visualizer
```

or

```bash
yarn add react-voice-visualizer
```

## Version 2.x.x Release Notes

**Breaking Changes:**
- Ref Handling Update: The library now manages audio references (audioRef) internally, streamlining the user experience.

**New Features:**
- Preloaded Audio Blob Support: Users can now set preloaded audio blobs using the `setPreloadedAudioBlob` function, enhancing versatility.

## [Demo App](https://react-voice-visualizer.vercel.app/)

Explore the [Demo Voice Visualizer App](https://react-voice-visualizer.vercel.app/) to see various features and functionalities in action. You can also refer to the demo app's source code for examples and inspiration.

## Usage

To use the VoiceVisualizer component, import the necessary hooks and components from the library. Here's an example for your `App` component:

```typescript jsx
import { useEffect } from "react";
import { useVoiceVisualizer, VoiceVisualizer } from "react-voice-visualizer";

const App = () => {
    const recorderControls = useVoiceVisualizer();
    const {
        recordedBlob,
        error,
    } = recorderControls;

    useEffect(() => {
        if (recordedBlob) {
            console.log(recordedBlob);
        }
    }, [recordedBlob, error]);

    useEffect(() => {
        if (error) {
            console.error(error);
        }
    }, [error]);

    return (
        <VoiceVisualizer controls={recorderControls} />
    );
};

export default App;
```

## Getting Started

1. Import required components and hooks.
2. Initialize recorder controls using the `useVoiceVisualizer` hook.
3. Manage audio recording and playback with provided state and functions.
4. Render the `VoiceVisualizer` component for real-time audio visualization.
5. Use buttons to start, pause, stop, and save recordings.

Ensure to include necessary CSS for customizing components and buttons.

## API Reference

### `useVoiceVisualizer()` Hook

A hook providing recorder controls and state for audio visualization.

#### Usage

```jsx
const recorderControls = useVoiceVisualizer();
```

#### Parameters (All optional)

| Parameter                | Type                     | Description                                                                                      |
|:-------------------------|:-------------------------|:-------------------------------------------------------------------------------------------------|
| `onStartRecording`       | `() => void`             | Callback when recording starts.                                                                  |
| `onStopRecording`        | `() => void`             | Callback when recording stops.                                                                   |
| `onPausedRecording`      | `() => void`             | Callback when recording is paused.                                                               |
| `onResumedRecording`     | `() => void`             | Callback when recording is resumed.                                                              |
| `onClearCanvas`          | `() => void`             | Callback when the canvas is cleared.                                                             |
| `onEndAudioPlayback`     | `() => void`             | Callback when audio playback ends.                                                               |
| `onStartAudioPlayback`   | `() => void`             | Callback when audio playback starts.                                                             |
| `onPausedAudioPlayback`  | `() => void`             | Callback when audio playback is paused.                                                          |
| `onResumedAudioPlayback` | `() => void`             | Callback when audio playback is resumed.                                                         |
| `onErrorPlayingAudio`    | `(error: Error) => void` | Callback when an error occurs during audio playback.                                             |

#### Returns

| Returns                             | Type                                                | Description                                                                                                                                                                                                 |
|:------------------------------------|:----------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `audioRef`                          | `MutableRefObject`<br/>`<HTMLAudioElement \| null>` | Reference to the audio element.                                                                                                                                                                              |
| `isRecordingInProgress`             | `boolean`                                           | Indicates if recording is in progress.                                                                                                                                                                      |
| `isPausedRecording`                 | `boolean`                                           | Indicates if recording is paused.                                                                                                                                                                           |
| `audioData`                         | `Uint8Array`                                        | Audio data for visualization.                                                                                                                                                                                |
| `recordingTime`                     | `number`                                            | Elapsed recording time in milliseconds.                                                                                                                                                                      |
| `mediaRecorder`                     | `MediaRecorder \| null`                             | MediaRecorder instance for recording audio.                                                                                                                                                                  |
| `duration`                          | `number`                                            | Duration of recorded audio in seconds.                                                                                                                                                                        |
| `currentAudioTime`                  | `number`                                            | Current playback time of the recorded audio in seconds.                                                                                                                                                     |
| `audioSrc`                          | `string`                                            | Source URL of the recorded audio file.                                                                                                                                                                       |
| `isPausedRecordedAudio`             | `boolean`                                           | Indicates if recorded audio playback is paused.                                                                                                                                                             |
| `isProcessingRecordedAudio`         | `boolean`                                           | Indicates if the recorded audio is being processed.                                                                                                                                                          |
| `isCleared`                         | `boolean`                                           | Indicates if the canvas has been cleared.                                                                                                                                                                    |
| `isAvailableRecordedAudio`          | `boolean`                                           | Indicates if recorded audio is available.                                                                                                                                                                     |
| `recordedBlob`                      | `Blob \| null`                                      | Recorded audio in Blob format.                                                                                                                                                                               |
| `bufferFromRecordedBlob`            | `AudioBuffer \| null`                               | Audio buffer from the recorded Blob.                                                                                                                                                                          |
| `formattedDuration`                 | `string`                                            | Formatted duration in the format 09:51m.                                                                                                                                                                      |
| `formattedRecordingTime`            | `string`                                            | Formatted current recording time in the format 09:51.                                                                                                                                                       |
| `formattedRecordedAudioCurrentTime` | `string`                                            | Formatted recorded audio current time in the format 09:51:1.                                                                                                                                                |
| `startRecording`                    | `() => void`                                        | Function to start audio recording.                                                                                                                                                                           |
| `togglePauseResume`                 | `() => void`                                        | Function to toggle pause/resume during recording and playback.                                                                                                                                               |
| `stopRecording`                     | `() => void`                                        | Function to stop audio recording.                                                                                                                                                                            |
| `saveAudioFile`                     | `() => void`                                        | Saves the recorded audio as a `webm` file format. Supports saving only in webm format.                                                                                                                      |
| `clearCanvas`                       | `() => void`                                        | Clears the visualization canvas.                                                                                                                                                                              |
| `setCurrentAudioTime`               | `Dispatch<SetStateAction<number>>`                  | Internal function to handle current audio time updates.                                                                                                                                                      |
| `error`                             | `Error \| null`                                     | Error object if any error occurred.                                                                                                                                                                           |
| `isProcessingOnResize`              | `boolean`                                           | Indicates if audio processing occurs during a resize event.                                                                                                                                                  |
| `isProcessingStartRecording`        | `boolean`                                           | Indicates that the start recording button has been pressed but recording has not yet commenced.                                                                                                             |
| `isPreloadedBlob`                   | `boolean`                                           | Indicates whether a preloaded audio blob is available.                                                                                                                                                       |
| `setPreloadedAudioBlob`             | `(blob: Blob) => void`                              | Sets a preloaded audio blob for seamless integration.                                                                                                                                                        |
| `_setIsProcessingAudioOnComplete`   | `Dispatch<SetStateAction<boolean>>`                 | Internal function to set processing audio completion state.                                                                                                                                                  |
| `_setIsProcessingOnResize`          | `Dispatch<SetStateAction<boolean>>`                 | Internal function to set processing on resize state.                                                                                                                                                        |

### `VoiceVisualizer` Component

A component that visualizes real-time audio waves during recording.

### Props for `VoiceVisualizer` Component

| Props                                             | Description                                                                                                                                                                                                                   | Default       | Type                         |
|:--------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------|:-----------------------------|
| **`controls`**                                    | Provides audio recording controls and states for visualization.                                                                                                                                                              | -             | `Controls` (Required)        |
| **`height`**                                      | Height of the visualization canvas.                                                                                                                                                                                          | `200`         | `string \| number` (Optional) |
| **`width`**                                       | Width of the visualization canvas.                                                                                                                                                                                           | `100%`        | `string \| number` (Optional) |
| **`backgroundColor`**                             | Background color of the visualization canvas.                                                                                                                                                                               | `transparent` | `string` (Optional)          |
| **`mainBarColor`**                                | Color of the main audio wave line.                                                                                                                                                                                          | `#FFFFFF`     | `string` (Optional)          |
| **`secondaryBarColor`**                           | Secondary color of the audio wave line.                                                                                                                                                                                     | `#5e5e5e`     | `string` (Optional)          |
| **`speed`**                                       | Animation speed of the audio visualization (Integer from 1 to 6).                                                                                                                                                          | `3`           | `number` (Optional)          |
| **`barWidth`**                                    | Width of each audio wave bar.                                                                                                                                                                                                | `2`           | `number` (Optional)          |
| **`gap`**                                         | Gap between each audio wave bar.                                                                                                                                                                                             | `1`           | `number` (Optional)          |
| **`rounded`**                                     | Border radius of the audio wave bars.                                                                                                                                                                                      | `5`           | `number` (Optional)          |
| **`isControlPanelShown`**                         | Displays the audio control panel.                                                                                                                                                                                            | `true`        | `boolean` (Optional)         |
| **`isDownloadAudioButtonShown`**                  | Displays the Download audio button.                                                                                                                                                                                          | `false`       | `boolean` (Optional)         |
| **`fullscreen`**                                  | Displays the visualization in fullscreen mode.                                                                                                                                                                              | `false`       | `boolean` (Optional)         |
| **`animateCurrentPick`**                          | Animates the current pick in the visualization.                                                                                                                                                                              | `true`        | `boolean` (Optional)         |
| **`onlyRecording`**                               | Shows the visualization only during voice recording.                                                                                                                                                                         | `false`       | `boolean` (Optional)         |
| **`isDefaultUIShown`**                            | Shows a default UI on Canvas before recording.                                                                                                                                                                               | `true`        | `boolean` (Optional)         |
| **`mainContainerClassName`**                      | CSS class name for the main container.                                                                                                                                                                                       | -             | `string` (Optional)          |
| **`canvasContainerClassName`**                    | CSS class name for the visualization canvas container.                                                                                                                                                                       | -             | `string` (Optional)          |
| **`isProgressIndicatorShown`**                    | Shows the progress indicator after recording.                                                                                                                                                                               | `true`        | `boolean` (Optional)         |
| **`progressIndicatorClassName`**                  | CSS class name for the progress indicator.                                                                                                                                                                                  | -             | `string` (Optional)          |
| **`isProgressIndicatorTimeShown`**                | Shows the progress indicator time.                                                                                                                                                                                          | `true`        | `boolean` (Optional)         |
| **`progressIndicatorTimeClassName`**              | CSS class name for the progress indicator time.                                                                                                                                                                             | -             | `string` (Optional)          |
| **`isProgressIndicatorOnHoverShown`**             | Shows the progress indicator on hover.                                                                                                                                                                                      | `true`        | `boolean` (Optional)         |
| **`progressIndicatorOnHoverClassName`**           | CSS class name for the progress indicator on hover.                                                                                                                                                                         | -             | `string` (Optional)          |
| **`isProgressIndicatorTimeOnHoverShown`**         | Shows the progress indicator time on hover.                                                                                                                                                                                 | `true`        | `boolean` (Optional)         |
| **`progressIndicatorTimeOnHoverClassName`**       | CSS class name for the progress indicator time on hover.                                                                                                                                                                    | -             | `string` (Optional)          |
| **`isAudioProcessingTextShown`**                  | Shows the audio processing text.                                                                                                                                                                                            | `true`        | `boolean` (Optional)         |
| **`audioProcessingTextClassName`**                | CSS class name for the audio processing text.                                                                                                                                                                               | -             | `string` (Optional)          |
| **`controlButtonsClassName`**                     | CSS class name for the Clear Button and Download Audio button.                                                                                                                                                              | -             | `string` (Optional)          |

## License

This library is distributed under the MIT License.
