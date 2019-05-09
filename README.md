# fractal-generator

This is a simple OpenGL fractal generator/visualizer. Some fractals are defined which are then displayed using OpenGL with zooming capability.

## Fractals
Here, fractals are defined by set theory and limits. The equation used is below:

<img src="https://latex.codecogs.com/gif.latex?z_n\in\text{F}\text{iff}\limsup_{n\to\\d}|z_{n+1}|\leq5" /> 

Where <img src="https://latex.codecogs.com/gif.latex?d" /> is the maximum number of iterations performed on <img src="https://latex.codecogs.com/gif.latex?z_n" />. Each iteration is defined by an arithmetic expression describing the relationship between <img src="https://latex.codecogs.com/gif.latex?z_n" /> and <img src="https://latex.codecogs.com/gif.latex?z_{n+1}" />, which is defined in terms of complex number arithmetic. 

A very large <img src="https://latex.codecogs.com/gif.latex?d" /> will render the fractal set with higher precision but may be difficult to see as points become "infinitely" thin; contrastingly, a very small <img src="https://latex.codecogs.com/gif.latex?d" /> will render the fractal set with very little granularity and is overall an inaccurate render. Suggested use case scenario is <img src="https://latex.codecogs.com/gif.latex?d\in[64,512]" /> as it's a good balance between clarity, visual pleasure, and of course execution time.

## Supported Fractals
Included are ten fractals, the first three have canonical names and the other seven are found through experimentation. The canonically named fractals alongside their iterative arithmetic is below:

<b>Mandelbrot Set</b>
- <img src="https://latex.codecogs.com/gif.latex?z_{n+1}=z_n^2+c" /> 

<b>Julia Set</b>
- <img src="https://latex.codecogs.com/gif.latex?z_{n+1}=z_n^2+k" /> 
- <img src="https://latex.codecogs.com/gif.latex?k" /> is some constant, here defined as <img src="https://latex.codecogs.com/gif.latex?(-0.835-0.232i)" />`

<b>Burning Ship Set</b>
- <img src="https://latex.codecogs.com/gif.latex?z_{n+1}=|z_n|^2+c" /> 

You can experiment with other fractals by editing `Set.cpp`: within `Set::iterate()` you can define the arithmetic expression which determines the set. Using a subset of complex number arithmetic, you can define new fractals. Available arithmetic operations are:

- `neg()` on a complex number `(a+bi)` returns `(-a-bi)`
- `inv()` on a complex number `(a+bi)` returns `(b+ai)`
- `abso()` on a complex number `(a+bi)` returns `(|a|+|b|i)`
- standard operators `+`, `-`, `*` and `^` will function as expected
- `^` only works with integer as second operand

For example, to get <img src="https://latex.codecogs.com/gif.latex?z_{n+1}=-z_n^3+z_n^2+c" />, you would hardcode in `(z^3).neg() + z^2 + c`, etc.

## Dependencies
- Freeglut
- Freeimage
- C++03 or later
- gcc
- X11 or other window manager

## Execution
    $ cd src
    $ g++ main.cpp -O2 -lGL -lGLU -lglut -lfreeimage -lX11 -std=c++0x
    $ /a.out <arg>
  
`<arg>` is the maximum depth (number of iterations) used to define fractal within the range `[32, 4096]`. Higher is slower but shows higher fidelity of the fractal set. This is the <img src="https://latex.codecogs.com/gif.latex?d" /> from before.

CLI will appear on execution detailing controls. `1` through `0` will cycle between fractals, `r` to reset, `s` to save screen capture to parent directory. Use mouse buttons to zoom in and out.

## Images
`todo`
