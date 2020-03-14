Letter symbols for physical quantities
======================================

`lettsymb`: a LaTeX package to provide standardized commands for the symbols of
physical quantities.


Purpose
-------

It is easy to confuse different symbols in science and engineering.  Is the
letter P the pressure or power here?  Is the letter omega the angular velocity
or the vorticity here?  The purpose of `lettsymb` is to allow LaTeX users to
worry more about the content of their documents and less about the
implementation, especially when particular symbols are complex to implement.
This package provides a simple set of commands to create custom commands for
the symbols of quantities, along with a library of commands using standardized
symbols of quantities.


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

    - Vectors and matrices

        - `\newVectorQuantity` (planned)

        - `\newMatrixQuantity` (planned)

    - Components of vectors

        - `\newComponentQuantity` (complete)

        - `\newNumberedComponentQuantity` (complete)

        - `\newLabeledComponentQuantity` (complete)

- A library of standardized symbols for quantities (incomplete)

    - General categories

        - Space and time (incomplete)
        
        - Mechanics (incomplete)
        
        - Thermodynamics (incomplete)

        - Electromagnetism (incomplete)
        
        - Light and radiation (planned)
        
        - Chemistry (incomplete)

        - Dimensionless numbers (incomplete)

    - Specialized categories

        - Fluid mechanics (planned)

- Package options to change the standardized symbols (planned)


How to use `lettsymb`
---------------------

To create a command, simply use one of the creation commands:

    \newQuantity{\qNumberOfBananas}{b}

Do not put any superscripts or subscripts in the final argument, since they
interfere with labels or exponents.

If the symbol you want to create contains a subscript or a label, use the
`\newLabeledQuantity` instead:

    \newLabeledQuantity{\qNumberOfApples}{n}{\mathrm{apples}}

This command will correctly place the subscript so that it does not interfere
with any additional labels.  Additional labels are available via the optional
argument:

    \qVolume[1]

    \qVolume[\mathrm{cube}]
    
    \qVolume[\mathrm{sphere}]

To use any symbol command from the standard library, you first must know its
name.  All names in the standard library follow a simple pattern:

1. A letter denoting the type of the symbol.

    - `d` for symbol of a dimension.

    - `q` for the preferred symbol of a quantity.

    - `a` for the alternative symbol of a quantity.  Alternative symbols can be
      used when you need two symbols for a type of quantity or when another
      quantity uses the same symbol as the preferred symbol.

    - `v` for the vector symbol of a quantity.

2. The name of the concept in `CamelCase` (like `SpecificHeat` for "specific
heat").

Combine these two and you can easily know the command for any given symbol of a
dimension or quantity.

Examples:

- `\dTime` is the command for symbol of the dimension of time and `\qTime` is
  the command for symbol of the quantity of time.

- `\qLength` is the command for the preferred symbol for the quantity of length
  and `\aLength` is the command for the alternative symbol for the quantity of
  length.

-------------------------------------------------------------------------------

Copyright © 2020 Andrew Trettel
