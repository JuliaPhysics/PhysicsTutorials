# PhysicsTutorials.jl
This package holds tutorials showing how to utilize Julia and its ecosystem for physics applications. Tutorials are available as PDFs, HTML webpages, and interactive Jupyter notebooks. The folder structure is `tutorials/<category>/<tutorial name>/`. Each tutorial folder is a Julia project, which can be `] activate`d and `] instantiate`d. For more information, please consult the [JuliaPhysics webpage](http://juliaphysics.github.io), which also lists a bunch of external tutorials.

## Table of Contents

* General
  * [Speeding up Quantum Mechanics - Matrix Types](https://juliaphysics.github.io/PhysicsTutorials.jl/tutorials/general/matrix_types/matrix_types.html)
  * [Quantum Ising Phase Transition](https://juliaphysics.github.io/PhysicsTutorials.jl/tutorials/general/quantum_ising/quantum_ising.html)
  
* Machine Learning
  * [Machine Learning the Ising Transition](https://juliaphysics.github.io/PhysicsTutorials.jl/tutorials/machine_learning/ml_ising/ml_ising.html)

## Interactive Jupyter Notebooks

To run the tutorials interactively in Jupyter notebooks, install the package and IJulia via

```
] add http://github.com/JuliaPhysics/PhysicsTutorials IJulia
```

and start/open the notebook server like

```julia
using PhysicsTutorials, IJulia
PhysicsTutorials.open_notebooks()
```

## Contributing

Supported source files for tutorials are Jupyter notebooks, Weave.jl files, or Literate.jl files.
To contribute a tutorial, clone the repository and put the source file into `tutorials/<category>/<tutorial_name>/` and name it `<tutorial_name>.ipynb` (extension `.jmd`/`.jl` for Weave/Literate sources). To trigger the generation process of all output formats, run the following code from within the repository root folder:

```julia
using Pkg; Pkg.activate(".")
using PhysicsTutorials
PhysicsTutorials.convert_tutorial("<category>","<tutorial_name>", PhysicsTutorials.NotebookSource())
```

For Weave or Literate sources, replace `PhysicsTutorials.NotebookSource()` by `PhysicsTutorials.WeaveSource()` or `PhysicsTutorials.LiterateSource()`, respectively.

### Title and Author Formatting
To have the title and author information of a tutorial formatted nicely, we special case the first two (non-empty) lines when parsing source files.

* The first line should indicate the title information as a level 1 header, indicated by `#`.
* The second line should specify the author information as a level 3 heading, i.e. `###`.

Hence, for notebook and Weave input files ([example](tutorials/machine_learning/ml_ising/ml_ising.ipynb)) you want the first two lines to be

```markdown
# My Awesome Tutorial
### John Doe
```

and for Literate input (see [this example](tutorials/general/matrix_types/matrix_types.jl))

```markdown
# # My Awesome Tutorial
# ### John Doe
```
