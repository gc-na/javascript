<!--
Meta Description: # SpeechSynthesisUtterance in JavaScript: Empowering Web Speech Synthesis ## Synopsis The `SpeechSynthesisUtterance` interface in JavaScript enables d...
Meta Keywords: speech, utterance, voice, speechsynthesis, speechsynthesisutterance
-->

# SpeechSynthesisUtterance in JavaScript: Empowering Web Speech Synthesis

## Synopsis
The `SpeechSynthesisUtterance` interface in JavaScript enables developers to create and control speech synthesis, allowing web applications to convert text to spoken words efficiently.

## Documentation

### Purpose
`SpeechSynthesisUtterance` is part of the Web Speech API, designed to enable text-to-speech functionality in web applications. This interface represents a speech request, encapsulating the text to be spoken and various speech parameters such as voice, pitch, rate, and volume.

### Usage
To utilize `SpeechSynthesisUtterance`, developers must first create an instance of the object, which can then be passed to the `SpeechSynthesis.speak()` method. The `SpeechSynthesis` interface controls the speech synthesis engine, allowing developers to manage speech playback.

### Properties
- **text**: The string of text that will be spoken.
- **lang**: A string representing the language of the utterance (e.g., "en-US" for American English).
- **voice**: A `SpeechSynthesisVoice` object that represents the voice used to speak the utterance.
- **pitch**: A number between 0 and 2 that defines the pitch of the voice (default is 1).
- **rate**: A number between 0.1 and 10 that defines the speed of speech (default is 1).
- **volume**: A number between 0 and 1 that defines the volume of speech (default is 1).

### Methods
- **SpeechSynthesis.speak(utterance)**: Enqueues the utterance for speech.
- **SpeechSynthesis.cancel()**: Stops any ongoing speech.
- **SpeechSynthesis.pause()**: Pauses the current speech.
- **SpeechSynthesis.resume()**: Resumes paused speech.

## Examples

### Basic Usage
```javascript
// Initialize the speech synthesis
const synth = window.speechSynthesis;

// Create a new utterance
const utterance = new SpeechSynthesisUtterance('Hello, world!');

// Set properties
utterance.lang = 'en-US';
utterance.pitch = 1.2;
utterance.rate = 1;
utterance.volume = 1;

// Speak the utterance
synth.speak(utterance);
```

### Using Different Voices
```javascript
// Check available voices
const voices = window.speechSynthesis.getVoices();
const utterance = new SpeechSynthesisUtterance('This is a test voice.');

// Select a voice
utterance.voice = voices.find(voice => voice.name === 'Google UK English Female');

// Speak the utterance
window.speechSynthesis.speak(utterance);
```

## Explanation
### Common Pitfalls
- **Voice Availability**: Available voices can vary by device and browser. Ensure to check for available voices before assigning one to avoid unexpected behavior.
- **Asynchronous Voice Loading**: The `getVoices()` method may return an empty array if called immediately after page load. Use the `voiceschanged` event to ensure voices are loaded.
- **Browser Support**: Not all browsers support the Web Speech API. Ensure to test compatibility across different environments.

### Additional Notes
- Adjusting the `pitch`, `rate`, and `volume` properties can significantly affect the user experience. Experiment with different settings to find the ideal combination.
- Consider implementing controls to pause and resume speech for better user interaction.

## One Line Summary
The `SpeechSynthesisUtterance` interface in JavaScript facilitates text-to-speech functionality, allowing developers to create dynamic and accessible web applications.