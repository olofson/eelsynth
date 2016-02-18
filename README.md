# EELSynth
A sound synthesizer prototyping platform implemented in EEL

EELSynth is a sound synthesizer prototyping platform implemented entirely in the scripting language [EEL](https://github.com/olofson/eel), using only SDL, and EEL’s standard vector maths and FFT module. It has a simple plugin API that supports audio input, audio output, and control input, allowing the creation of various synths and effects.

As a side effect of various experiments and debugging, EELSynth has grown into a small application with a GUI and a rudimentary multi-track sequencer.

The most interesting part by far at this point is probably the IFFT based “massively additive” synthesizer, which turned out to be a lot more effective than expected. ([Small demo](https://soundcloud.com/david-olofson/eelsynth-ifft-flutesong)) It's based on the idea of scripts that control large numbers of oscillators that "paint" their output into FFT spectra, which are then converted into audio through windowed overlap-add FFT. That is, actual oscillator banks - not FFT bins. It's all simple scripts running in real time. No resynthesis. No precalculated spectra.
