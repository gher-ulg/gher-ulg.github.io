# Installation


* Install [Julia](https://julialang.org/downloads/). You will need the latest version 0.6. (Older versions are not supported)
* Install `divand`. Launch julia and in the terminal issue the following command:

```julia
Pkg.clone("https://github.com/gher-ulg/divand.jl")
```

Copying and pasting commands in a terminal:
* Windows user should have a look at this to [enable the quick edit mode](https://blogs.msdn.microsoft.com/adioltean/2004/12/27/useful-copypaste-trick-in-cmd-exe/) to facilitate copying and pasting commands. 

* It is highly recommended to install also `IJulia` for the workshop. For the plotting we will use `PyPlot`. These two packages can be installed using the following commands. 

```julia
Pkg.add("PyPlot")
Pkg.add("IJulia")
```
Installation can take a couple of minutes and will tabe about 3 GB of disk space.


# Testing your installation

* In the Julia terminal, please issue the following commands to test `divand`:

```julia
Pkg.test("divand");
```
All tests should succseed.

* Testing `PyPlot`. Again in the Julia terminal, please issue the following commands:

```julia
using PyPlot
plot(1:10)
```

A new window should open with a straight line.

* Testing `IJulia`. Issue the following commands in a Julia terminal:

```julia
using IJulia
notebook()
```

A new browser window should open. Then, click on New => Julia 0.6. In the textbox, type 1+2 and then hit `Control-Enter`. The answer should be 3!





---

JM version:

Install anaconda: [https://conda.io/docs/user-guide/install/index.html](https://conda.io/docs/user-guide/install/index.html) 

Install IJulia:
```julia
Pkg.add("IJulia")
```

Install Plots:
```julia
Pkg.add("Plots")
```

Clone `divand` into the v0.6 julia directory:
```bash
cd .julia/v0.6/
git clone git@github.com:gher-ulg/divand.jl.git
```

Install Interpolations:
```julia
Pkg.add ("Interpolations")
```
(remove if we add a *required* into divand module).

Install PyPlot:
```julia
Pkg.add("PyPlot")
```

### First steps with Jupyter and Julia

When modifying the code, restart the kernel to make sure latest version is
used (remember, julia does some compilations).


#### Updating julia
1. Download binaries, install as usual.     
2. Run in Julia (not IJulia of Jupyter): `Pkg.build("IJulia")` or ??
`Pkg.add("IJulia")``
3. Then in IJulia `Pkg.update()`


# Troubleshooting

Depending on your current Julia setup, installing divand might ask for
installation of additional packages. This will clearly been shown
for example
```julia
LoadError: ArgumentError: Module Roots not found in current path.
Run `Pkg.add("Roots")` to install the Roots package.
```

## C runtime library when calling PyPlot

`R6034 an application has made an attempt to load the C runtime library incorrectly` on Windows 10 with julia 0.6.1, matplotlib 2.1.0, PyPlot 2.3.2:

```julia
ENV["MPLBACKEND"]="qt4agg"
```
You can put this line in a file `.juliarc.jl` placed in your home directory (the output of `homedir()` in Julia).