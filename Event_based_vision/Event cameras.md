- We are using our vision in the same way as Muybridge invented it.
![[Pasted image 20231022210518.png]]
- He took multiple pictures of a horse rider at different intervals of time with different cameras.
- Running these images with a fast enough frequency would result in a video.
- Later M. Mahowald and C. Mead in 1990 invented the neuromorphic vision chip.
- Two types of cameras:
	- Standard, frame based camera
		- Puts out a sequence of images called frames
	- Event based camera
		- Outputs an array of events based on changing intensity per pixel.
		- We can visualize these events in space-time.
![[Pasted image 20231022211451.png]]

- The event camera working:
	- Consider a single pixel.
	- it will have a given pixel value given by:
		$$ log I(x,t) - log I(x,t - \triangle (t)) = \pm C$$
	- If this value is greater or less than a given threshold, the pixel would return an on or an off event respectively.
		![[Pasted image 20231022220744.png]]
	- So now what are events?
		$$ e = (x, y, t, p) $$
	- t is time in microseconds.
	- p is the polarity of the events and is given by:
		$$ p = sgn \left( \delta I(x, y, t) \over \delta t \right) \in \{ +1 , -1 \} (binary) $$
- Though event cameras work on brightness changes, it is not the same as the brightness increments/decrements that we get by subtracting two standard frames.
	- This is because event cameras are asynchronous while standard frames are synchronous.
- There are two types of event based on the sensor design.
	- Change detection (CD)
		- Gets the change in pixel.
		- Binary events.
	- Exposure measurement (EM)
		- Gets the exposure of the pixel, the change in happening.
		- Grayscale events.
	- We can also make augmented events (AE).
		- e = (x, y, t, p, extra)
		- extra could be anything that can be appended in the event tuple such as event lifetime, optical flow, depth, etc.
	- 