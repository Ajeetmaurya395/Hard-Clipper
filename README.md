# HardClipper

A professional-grade Hard Clipping Distortion plugin built from scratch using C++ and the JUCE Framework.

## Overview
HardClipper is a dynamic distortion effect that applies digital clipping to an incoming audio signal. Unlike standard gain plugins, this implementation uses a custom DSP algorithm to "chop" signal peaks, creating aggressive harmonics and a square-wave-like tonality.

It was built to demonstrate real-time audio processing, buffer manipulation, and VST3 architecture.

## Features
* Adjustable Drive: Boosts input signal gain from 0dB to +20dB to push audio into saturation.
* Hard Limiting: Implements a strict clamping algorithm (Sample values capped at -0.5 to 0.5) to ensure consistent distortion character.
* Real-Time Safety: Optimized DSP loop with zero memory allocation during the audio callback (processBlock), ensuring no audio dropouts or glitches.
* Stereo Processing: Independently processes Left and Right channels.

## Tech Stack
* Language: C++ (C++17)
* Framework: JUCE 7
* Format: VST3 / AU
* Tools: Projucer, Xcode/Visual Studio

## The DSP Logic
The core of the effect runs inside the processBlock loop. It iterates through the audio buffer and applies the following logic:

// Simplified Logic
float currentSample = buffer[sample];
currentSample *= drive; // Boost gain

// Hard Clip
if (currentSample > threshold)
    currentSample = threshold;
else if (currentSample < -threshold)
    currentSample = -threshold;

## How to Build
1. Clone the repository:
   git clone https://github.com/Ajeetmaurya395/HardClipper.git
2. Open HardClipper.jucer using the Projucer.
3. Select your exporter (Xcode for Mac, Visual Studio for Windows).
4. Open the IDE and hit Build.
5. Load the resulting .vst3 file into FL Studio or Ableton Live.

Created by Ajeet Maurya
