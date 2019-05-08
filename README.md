# fractal-generator

## Dependencies
- Freeglut
- Freeimage
- C++03 or later
- gcc
- X11 or other window manager

## Execution
    $ g++ Source.cpp -O2 -lGL -lGLU -lglut -lfreeimage -lX11 -std=c++0x
    $ /a.out <arg>
  
`<arg>` is the maximum depth (number of iterations) used to define fractal within the range `[32, 4096]`. Higher is slower but better representation of the fractal set.

CLI will appear on execution detailing controls. `1` through `0` will cycle between fractals, `r` to reset, `s` to save screen capture to parent directory. Use mouse buttons to zoom in and out.

## Fractals
Fractals are defined by set theory and limits. The equation used is below:

<img src="https://latex.codecogs.com/gif.latex?z_n\in\text{F}\text{iff}\limsup_{n\to\\d}|z_{n+1}|\leq5" /> 

Where `d` is the argument provided to the application. The arithmetic expression describing the relationship between <img src="https://latex.codecogs.com/gif.latex?z_n" /> and <img src="https://latex.codecogs.com/gif.latex?z_{n+1}" /> is described in terms of complex number arithmetic.

Included are ten fractals, the first three have canonical names and the other seven are found through experimentation. The canonically named fractals are below:

<b>Mandelbrot Set</b>
- <img src="https://latex.codecogs.com/gif.latex?z_{n+1}=z_n^2+c" /> 

<b>Julia Set</b>
- <img src="https://latex.codecogs.com/gif.latex?z_{n+1}=z_n^2+(-0.835-0.232i)" /> 

<b>Burning Ship Set</b>
- <img src="https://latex.codecogs.com/gif.latex?z_{n+1}=|z_n|^2+c" /> 

You can experiment with other fractals by editing `Set.cpp`: within `Set::iterate()` you can define the arithmetic expression which determines the set. Using a subset of complex number arithmetic, you can define new fractals. Available arithmetic operations are:

- `neg()` on a complex number `(a+bi)` returns `(-a-bi)`
- `inv()` on a complex number `(a+bi)` returns `(b+ai)`
- `abso()` on a complex number `(a+bi)` returns `(|a|+|b|i)`
- standard operators `+`, `-`, `*` and `^` will perform as expected
- `^` only works as integer as second operand
