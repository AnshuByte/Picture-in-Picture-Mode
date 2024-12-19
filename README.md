# Picture-in-Picture Mode

This project demonstrates how to enable Picture-in-Picture (PiP) mode in modern browsers using JavaScript. Picture-in-Picture allows users to watch videos in a small floating window while interacting with other applications or parts of a webpage.

## Features
- Prompt users to select a media stream (e.g., screen sharing).
- Display the media stream in a video element.
- Enable Picture-in-Picture mode for the video element.

## Technologies Used
- HTML
- JavaScript
- Modern Web APIs: `navigator.mediaDevices.getDisplayMedia`, `videoElement.requestPictureInPicture`

## How It Works
1. **Media Stream Selection**:
   - Users are prompted to select a media stream, such as their screen, window, or browser tab.
   - The selected stream is set as the source for a video element.
2. **Picture-in-Picture Activation**:
   - Users click `start` button to enable Picture-in-Picture mode.
   - The video is displayed in a floating, resizable window that stays on top of other applications.

## Code Explanation

### HTML Elements
```html
<video id="video" controls></video>
<button id="button">Start</button>
```
- video: Displays the media stream.
- button: Triggers Picture-in-Picture mode.
### JavaScript Implementation
Media Stream Selection
```javascript
async function selectMediaStream() {
    try {
        const mediaStream = await navigator.mediaDevices.getDisplayMedia();
        videoElement.srcObject = mediaStream;
        videoElement.onloadedmetadata = () => {
            videoElement.play();
        };
    } catch (error) {
        console.error('Error accessing media devices:', error);
    }
}
```
- Prompts the user to select a media stream.
- Sets the stream as the source of the video element.
### Picture-in-Picture Activation
```javascript
button.addEventListener('click', async () => {
    button.disabled = true;
    await videoElement.requestPictureInPicture();
    button.disabled = false;
});
```
- Disables the button to prevent multiple clicks.
- Activates Picture-in-Picture mode for the video.
- Re-enables the button after PiP mode starts.
### Initialization
```javascript
selectMediaStream();
```
- Automatically prompts the user to select a media stream on page load.
### Usage
- Open the project in a browser that supports Picture-in-Picture.
- Click the button to select a media stream.
- Watch the selected stream in a floating window using Picture-in-Picture mode.
### Browser Support
This project works in modern browsers that support the following APIs: 
- `navigator.mediaDevices.getDisplayMedia`
- `HTMLVideoElement.requestPictureInPicture`
### Acknowledgments
- MDN Web Docs for detailed API documentation.
- Web APIs that enable seamless user experiences.
