All of these are open-sourced. If used as a template for another package, please give credit! Anyone and everyone can use any of these in their papers! 

The Documents in this repository:

physdiacs.sty, physobj.sty

Beginning with physdiacs.sty, the diacritics for my physics notation, this package requires tikz. Thus, here's the commands to add this to
your LaTeX document:

\usepackage{tikz}

\usepackage{physdiacs}

Here's the commands:
 - \td commands: Most combinations of length, area, volume, angle, and solid angles can be directly accessed within a tikz drawing
   environment through \td commands. This is for customization of diacritic placement if necessary and only available within a tikz environment.
- \CH and \DC commands: This is the raw character that merges diacritics together. The \DC command is the direct diacritic on the character needed,
  applied as \DC___ {X}, where X is the letter that needs the diacritics. 
  - All \DC commands are defined as "\newcommand{\DC____}[1]{\CH____ {#1}}"
- All \td, \CH, and \DC commands are written in concatenation. First, start with the raw command (\td ,\CH, \DC). Then:
    - If multiplying by length, concatenate a capital L to the right of the command (\tdL) or if dividing by length, concatenate a lowercose L to the
      right of the command (\tdl). Only one L may be in the command. \tdLl is not a command.
    - Similarly, concatenate an "A" or "a" if multiplying or dividing by area, respectively, then a "V" or "v" if multiplying or dividing by volume,
      then an "N" or "n" when multiplying or dividing an angle, and an "O" or "o" when multiplying or dividing by a solid angle.
    - Then, concatenate a "t" if you need a tilde, then a "u" if you want to reverse only Upsilon units (a breve), an "s" when reversing only seconds
      units (upside-down breve), or an "r" when reversing both Upsilon and second units (a ring). Afterwords, concatenate an "i" if you are inverting
      all units (a macron).
    - Afterwords, the arguments.
        - For \td, the format is \td___ {x displacement in pt's} {y displacement in pt's} Example: \tdLaVnO {1pt} {2pt}
        - For \CH, no arguments exist
        - For \DC, the format is \DC___ {X}. For example, pressure is \DCa {F}. 
    - In the end, the command should look like "\DClAvNti". A worst case scenario: \CHLAVNOtiu
  
