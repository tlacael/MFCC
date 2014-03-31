MFCC
====

MFCC extractor class for use with real-time audio callbacks.


This code has been adapted from libmfcc (https://code.google.com/p/libmfcc/) 
to work in the context of a real-time audio callback. As a C++ class, and 
MFCC specific calculations are done at initialization to minimize calculations
in the callback. Although it works, there is definitely more that can be done
to streamline this further.

Example call:
```c++

int sr = 44100;
int numFilters = 48;
FFTlen = 512;
int specLen = FFTlen/2+1;
int numCoeffs = 20;

float *spectrum = new float[specLen];
float *mfccs = new float[numCoeffs];

// calculate magnitude-spectrum of a frame of audio

MFCC mfcc;
mfcc.init(sr, numFilters, specLen, numCoeffs);
mfcc.getCoefficients(spectrum, mfccs);

```
