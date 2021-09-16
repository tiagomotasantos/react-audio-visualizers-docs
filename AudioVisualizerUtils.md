---
layout: default
title: "AudioVisualizerUtils"
---

# `AudioVisualizerUtils`

The `AudioVisualizerUtils` class contains utility functions to help deal with common audio tasks.

Here's a list of the functions available:

- [`map`](#map)
- [`filterFrequencies`](#filterfrequencies)
- [`getFrequencyInterval`](#getfrequencyinterval)


## `map`

**map(n, start1, stop1, start2, stop2): number**

The `map` function maps a number value **n** from one interval, **[start1, stop1]**, to another interval, **[start2, stop2]**.

## `filterFrequencies`

**filterFrequencies(lowFrequency, highFrequency, dataArray, sampleRate): Uint8Array**

The `filterFrequencies` function returns a `Uint8Array` containing the frequency data from **dataArray** but filtered between **lowFrequency** and **highFrequency**. This function also requires the **sampleRate** of the audio. The default value for low frequency is **20** and the default value for high frequency is **20000** in Hz.

## `getFrequencyInterval`

**getFrequencyInterval(lowFrequency, highFrequency, nBars, dataArray, sampleRate): number**

The `getFrequencyInterval` function returns a `number` representing the interval required to cover the **dataArray** **nBars** times, having in consideration the frequency range passed.

See an example bellow:

```jsx
import { AudioVisualizerUtils } from 'react-audio-visualizers-core';

const sampleRate = 44000;
const lowFrequency = 20;
const highFrequency = 20000;
const nPoints = 5;
const dataArray = new Uint8Array(Array.from(Array(sampleRate / 2), () => Math.random() * 255));
const output = AudioVisualizerUtils.getFrequencyInterval(lowFrequency, highFrequency, nPoints, dataArray, sampleRate);

// output: 3996 
console.log(output);
```

For an audio with sample rate of 44000Hz, filtered between 20Hz and 20000Hz, the function produces the value 3996, which means that if we want to divide the frequency data in 5 points we can iterate the **dataArray** with a 3996 interval.