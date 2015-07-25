# ChucK programming

## What is it?
ChucK is a programming language for real-time sound synthesis and music creation. It is open-source and freely available on MacOS X, Windows, and Linux. ChucK presents a unique time-based, concurrent programming model that's precise and expressive (we call this strongly-timed), dynamic control rates, and the ability to add and modify code on-the-fly. In addition, ChucK supports MIDI, OpenSoundControl, HID device, and multi-channel audio. It's fun and easy to learn, and offers composers, researchers, and performers a powerful programming tool for building and experimenting with complex audio synthesis/analysis programs, and real-time interactive music.

You can download it from here:
http://chuck.cs.princeton.edu/release/

## First program
Simple program which connects to DAC (sound card) and plays sin for 2 seconds

## Second program
This should sound like computer mainframes in old sci-fi movies. Two more things to note here. (1) We are advancing time inside the loop by 100::ms durations. (2) A random value between 30.0 and 1000.0 is generated and 'assigned' to the oscillator's frequency, every 100::ms.


## Thrid program
```
      // impulse to filter to dac
      Impulse i => BiQuad f => dac;
      // set the filter's pole radius
      .99 => f.prad;
      // set equal gain zero's
      1 => f.eqzs;
      // initialize float variable
      0.0 => float v;

      // infinite time-loop
      while( true )
      {
          // set the current sample/impulse
          1.0 => i.next;
          // sweep the filter resonant frequency
          Std.fabs(Math.sin(v)) * 4000.0 => f.pfreq;
          // increment v
          v + .1 => v;
          // advance time
          100::ms => now;
      }
```
