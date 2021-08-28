Letter symbols for physical quantities
======================================

`lettsymb`: a LaTeX package to provide standardized commands for the symbols of
physical quantities.


Purpose
-------

`lettsymb` allows LaTeX users to worry more about the content of their
mathematics and less about the implementation.  This package provides a simple
set of commands to create custom commands for the symbols of quantities, along
with a library of commands using standardized symbols of quantities.  Instead
of typing `F` for force, users can use `\qForce` instead for added clarity.
These kind of commands allow the document to be read in natural language and
make changing the notation later much easier.


Features (and status)
---------------------

- Commands to create symbol commands (incomplete)

    - Dimensions

        - `\newDimension` (complete)

    - Quantities

        - `\newQuantity` (complete)

        - `\newLabeledQuantity` (complete)

        - `\newExtensiveQuantity` (complete)

        - `\newSpecificQuantity` (complete)

        - `\newMolarQuantity` (complete)

        - `\newDimensionlessNumber` (complete)

        - `\newLabeledDimensionlessNumber` (complete)

    - Vectors

        - `\newVectorQuantity` (complete)

    - Components of vectors

        - `\newComponentQuantity` (complete)

        - `\newNumberedComponentQuantity` (complete)

        - `\newLabeledComponentQuantity` (complete)

    - Index notation

        - `\newIndexNotationQuantity` (complete)

- A library of standardized symbols for quantities (incomplete)

    - General subjects

        - Mathematical quantities (incomplete)

        - Space and time (incomplete)
        
        - Mechanics (incomplete)
        
        - Thermodynamics (incomplete)

        - Electromagnetism (incomplete)
        
        - Light and radiation (incomplete)
        
        - Chemistry (incomplete)

        - Dimensionless numbers (incomplete)

        - Index notation (incomplete)

    - Specialized subjects

        - Fluid mechanics (incomplete)

- Package options to change the standardized symbols (incomplete)

    - `bm` - use `bm` package for bold vector symbols (default)

    - `nostrikethroughvolume` - use a plain V for the symbol for volume
      (default)

    - `pmb` - use the `\pmb` command from the `amsmath` package for bold vector
      symbols

    - `strikethroughvolume` - use a strikethrough V for the symbol for volume


Usage
-----


### Loading the package

```latex
\usepackage{lettsymb}
```


### Creating symbol commands

To create a command, simply use one of the creation commands:

```latex
\newQuantity{\qHeight}{h}
```

The first argument is the name of the command to create, and the second
argument is the symbol to use.  Do not put any superscripts or subscripts in
the second argument, since they interfere with labels or exponents.

If the symbol you want to create contains a subscript or a label, use
`\newLabeledQuantity` instead:

```latex
\newLabeledQuantity{\qHeightOfTree}{h}{\mathrm{tree}}
```

This command will correctly place the subscript so that it does not interfere
with any additional labels.  Additional labels are available via the optional
argument:

```latex
\qVolume[1]

\qVolume[\mathrm{cube}]

\qVolume[\mathrm{sphere}]
```

The commands `\newExtensiveQuantity`, `\newSpecificQuantity`, and
`\newMolarQuantity` are used to create extensive and intensive variables.  They
follow how `\newQuantity` works but also change the given symbol automatically
to adjust it to a standardized form, to better distinguish between extensive
and intensive quantities.


### Using symbol commands

To use any symbol command from the standard library, you first must know its
name.  All names in the standard library follow a simple pattern:

1. A letter denoting the type of the symbol.  Different prefixes often require
different arguments, optional and otherwise.

    - `d` for symbol of a dimension.  The optional argument is the exponent.

    - `q` for the preferred symbol of a quantity.  The optional argument is the
      label.

    - `a` for the alternative symbol of a quantity.  Alternative symbols can be
      used when you need two symbols for a type of quantity or when another
      quantity uses the same symbol as the preferred symbol.  The optional
      argument is the label.

    - `v` for the vector symbol of a quantity.  The optional argument is the
      label.

    - `c` for the component symbol of a vector quantity.  The required argument
      is the dimension number.

    - `i` for the index notation symbol of a quantity.  The required argument
      is the lower indices and the optional argument is the upper indices.

2. The name of the concept in `CamelCase` (like `SpecificHeat` for "specific
heat").  Note that only ASCII letters are accepted, so "Damköhler number"
becomes `DamkoehlerNumber`, for example.  Apostrophes, dashes, and other
punctuation are also dropped ("Poisson's ratio" becomes `PoissonsRatio`).

Combine these two and you can easily know the command for any given symbol of a
dimension or quantity.

Examples:

- `\dTime` is the command for symbol of the dimension of time and `\qTime` is
  the command for symbol of the quantity of time.

- `\qLength` is the command for the preferred symbol for the quantity of length
  and `\aLength` is the command for the alternative symbol for the quantity of
  length.

Finally, you can use any symbol command just as you would use any variable when
writing equations.

```latex
Newton's second law is
%
\begin{equation}
    \vForce
    =
    \qMass
    \vAcceleration
    \,.
\end{equation}
```

```latex
The speed of sound in an ideal gas is
%
\begin{equation}
    \qSpeedOfSound[\mathrm{ig}]^2
    =
    \qHeatCapacityRatio
    \qSpecificGasConstant
    \qTemperature
    \,.
\end{equation}
```

```latex
\begin{equation}
    \frac{
        \partial
        \cRectangularVelocity{1}
    }{
        \partial
        \cRectangularCoordinate{1}
    }
    +
    \frac{
        \partial
        \cRectangularVelocity{2}
    }{
        \partial
        \cRectangularCoordinate{2}
    }
    =
    0
    \,.
\end{equation}
```


### Using index notation (summation convention)

Index notation commands operate differently.  Each index notation command
accepts the lower indices as the required argument and the upper indices as the
optional argument.  Many writers only use the lower indices (for rectangular
coordinates only), so this choice minimizes the amount of typing for that
particular case while still allowing for more general usage.

```latex
\begin{equation}
    \iAlternatingSymbol{ijk}
    \iAlternatingSymbol[imn]{}
    =
    \iKroneckerDelta[m]{j}
    \iKroneckerDelta[n]{k}
    -
    \iKroneckerDelta[n]{j}
    \iKroneckerDelta[m]{k}
    \,.
\end{equation}
```

TODO: Switch from this interface to something like `\iQuantity{iJ}`, where `i`
is a lower index and `J` is an upper index.  Using lowercase
letters for lower indices and uppercase letters for upper indices should
simplify the use of these commands.


-------------------------------------------------------------------------------

Copyright © 2020-2021 Andrew Trettel

This work may be distributed and/or modified under the conditions of the LaTeX
Project Public License, either version 1.3 of this license or (at your option)
any later version.  The latest version of this license is in
<http://www.latex-project.org/lppl.txt> and version 1.3 or later is part of all
distributions of LaTeX version 2005/12/01 or later.

This work has the LPPL maintenance status `author-maintained`.

The Current Maintainer of this work is Andrew Trettel.

This work consists of the files lettsymb.sty and README.md.
