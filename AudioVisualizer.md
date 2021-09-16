---
layout: default
title: "AudioVisualizer Component"
---

# `<AudioVisualizer>`

The `<AudioVisualizer>` component is part of react-audio-visualizers-core package. It is responsible to place the visualizer rendering logic inside the canvas and mainly to take care of audio functionality through the Web Audio API, like loading the audio and interacting with it (e.g. play, pause, change volume, ...).

```jsx
import { AudioVisualizer, AudioVisualizerCommonProps } from 'react-audio-visualizers-core';

export const YourVisualizer = (commonProps: AudioVisualizerCommonProps) => (
    <AudioVisualizer {...commonProps}>
        <YourVisualizerRenderComponent />
    </AudioVisualizer>
);
```

Every prop (besides children) that `<AudioVisualizer>` receives is passed from the visualizer component, so every visualizer should accept them. These are referred as common props. 

Here's a list of common props:

- [`chidlren`](#children)
- [`audio`](#audio)
- [`canvasProps`](#canvasprops)
- [`smoothingTimeConstant`](#smoothingtimeconstant)
- [`fftSize`](#fftsize)
- [`volume`](#volume)
- [`iconsColor`](#iconsColor)
- [`showMainActionIcon`](#showmainactionicon)
- [`showLoaderIcon`](#showloadericon)
- [`backgroundColor`](#backgroundcolor)
- [`backgroundImage`](#backgroundimage)
- [`mainActionRender`](#mainactionrender)
- [`onEvent`](#onevent)

## `children`

The children is required and is a `ReactElement` that is passed as children to the `Canvas` component of react-three-fiber and it should contain the rendering logic of the visualizer besides being a component that react-three-fiber can handle.

## `audio`

The `audio` prop is required and can either be a JavaScript `File`, a `string` with a path/URL to the audio file or an `ArrayBuffer` with audio data.

## `canvasProps`

The `canvasProps` is an object which type comes from react-three-fiber and provides properties and methods from [`HTMLCanvasElement`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement).

## `smoothingTimeConstant`

A double value between 0 and 1 that averages the current buffer with the last buffer processed by the `AnalyserNode`. Check the offical [documentation](https://developer.mozilla.org/en-US/docs/Web/API/AnalyserNode/smoothingTimeConstant) for more information.

## `fftSize`

Property from the `AnalyserNode` that represents the number of samples used to perform a Fast Fourier Transform. Check the offical [documentation](https://developer.mozilla.org/en-US/docs/Web/API/AnalyserNode/fftSize) for more information.

## `volume`

A property from the [`GainNode`](https://developer.mozilla.org/en-US/docs/Web/API/GainNode) that represents the amount of gain to apply. Check the offical [documentation](https://developer.mozilla.org/en-US/docs/Web/API/GainNode/gain) for more information.

## `iconsColor`

A `string` that accepts a [CSS color](https://www.w3schools.com/css/css_colors.asp) used in the play, pause and loader icons.

## `showMainActionIcon`

A `boolean` value to show/hide the icons for the main play/pause action.

## `showLoaderIcon`

A `boolean` value to show/hide the icon for the loader.

## `backgroundColor`

A `string` that accepts a [CSS color](https://www.w3schools.com/css/css_colors.asp) used as background color of the canvas. It overwrites the background color specified in [`canvasProps`](#canvasprops).

## `backgroundImage`

A `string` that accepts an URL pointing to an image to use as background. It overwrites the [`backgroundColor`](#backgroundcolor).

## `mainActionRender`

A function that receives an object with `play` and `pause` properties, and has to return an object with `id` and `node` properties. The `play` and `pause` are the functions used to trigger the main action. The returned `id` should be the element id of a container to render the `node`. This is used to add your own UI to the play/pause main action by overwriting the default UI.

See an example bellow:


```jsx
import { AudioVisualizer, AudioVisualizerCommonProps } from 'react-audio-visualizers-core';

const mainActionRender = ({ play, _ }) => ({
    id: 'mainActionContainer',
    node: <button onClick={play}>Play</button>,
});


export const YourVisualizer = (commonProps: AudioVisualizerCommonProps) => (
    <div>
        <AudioVisualizer {...commonProps} mainActionRender={mainActionRender}>
            <YourVisualizerRenderComponent />
        </AudioVisualizer>
        <div id="mainActionContainer">
        </div>
    </div>
);
```

## `onEvent`

A function that receives an event of type `AudioVisualizerEvents` and a payload with information of the event. This is used to execute custom logic when an event occurs inside the audio visualizer.

See an example bellow:


```jsx
import { AudioVisualizer, AudioVisualizerCommonProps, AudioVisualizerEvents } from 'react-audio-visualizers-core';

const onEvent = (event, payload) => {
    if (event === AudioVisualizerEvents.PLAYING) {
        console.log('The audio started playing!!');
    } else if (event === AudioVisualizerEvents.ERROR) {
        console.log('The following error occured:', payload);
    } 
};

export const YourVisualizer = (commonProps: AudioVisualizerCommonProps) => (
    <AudioVisualizer {...commonProps} onEvent={onEvent}>
        <YourVisualizerRenderComponent />
    </AudioVisualizer>
);
```