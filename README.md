# Layered Sine
Fills a canvas with sine wave(s). Usable in browser.

## Usage
Install this package by:
```bash
npm i layered-sine-browser
```
Import the package in your script by:
```ts
import { SineWave, FillMode, animateSines, animateSinesFrames, drawSine } from "layered-sine"
```
The functions and classes are defined as follows:
```ts
// Draws a sine wave onto the canvas. Returns the drawn canvas.
function drawSine(wave: SineWave, canvas: HTMLCanvasElement, t = 0): HTMLCanvasElement
```
- `wave`/`waves`: Sine wave(s) to draw.
- `canvas`: Background canvas.
- `t`: Time. Also determines the phase of wave.

```ts
class SineWave {
	amplitude: number;
	wavelength: number;
	waveNum: number;
	period: number;
	nFreq: number;
	phase: number;
	y: number;
	fill: FillMode;
	color: number;

	constructor(amplitude: number, wavelength: number, period: number, phase: number, y: number) {
		this.amplitude = amplitude;
		this.wavelength = wavelength;
		this.waveNum = 2 * Math.PI / wavelength;
		this.period = period;
		this.nFreq = 2 * Math.PI / period;
		this.phase = phase;
		this.y = y;
	}
}
```
This is in the form of `A sin( kx - wt + p ) + y`, where:
- `A` (Amplitude) = `amplitude`
- `k` (Wave Number) = 2π / `wavelength`
- `w` (Natural Frequency) = 2π / `period`
- `p` (Phase) = `phase` (in radian)
- `y` (Y Offset) = `y` (Y-axis is flipped in rendering)

Other properties of `SineWave` class:
- `fill`: `FillMode` of the wave, can be `LINE` (0), `UP` (1) or `DOWN` (2).
- `color`: Color of the wave. Must be between `0x000000` and `0xFFFFFF`.

Here's the `FillMode` enum:
```ts
enum FillMode {
	LINE = 0,
	UP = 1,
	DOWN = 2
}
```

## License
GNU GPL v3