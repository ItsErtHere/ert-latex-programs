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


 physobj.sty: Commands for concepts and characters in physics that are not base letters (Mostly tilde variations). This requires the package upgreek.
 Therefore, to add this to your document, write

 \usepackage{upgreek}

 \usepackage{tikz}

 \usepackage{physobj}

 Here's the accessory commands:
  - \ups {X}: X_{\upupsilon}
  - \upi: \upupsilon
  - \uns {X}: X_{\upupsilon}^n
  - \dif: The "d" for differentiation
  - \diff {a} {b}: the first derivative of "a" according to "b" in Leibnez form (dy/dx)
  - \dff {a} {b} {c}: The c'th derivative of "a" according to "b" in Leibnez form
  - \frun {n}: (m/Upsilon)^n
  - \units {x}: \left\[ #1 \right\]
  - \frcu {a} {b} {c}: \units{\frac{a}{b}\frun{c}}
  - \frcn {a} {b} {c}: \frac{a}{b}\frun{c}
  - \Ukg, \Us, \Um, \UK, \UC, \Umol, \Ulx, \Urad, \Utb, \Ulm, \UJ, \UPa, \UA: Return their corresponding SI unit as \text text in math mode.
  - \mpm: Tikz overlapping of the plus-minus sign (\pm) and the minus-plus sign (\mp).

Here's the base tilde characters. Any letter without specified units is unused.
    - The letters with SI units for their normal forms are listed below with their units:
     - D: Dosage (U^2/s^2)
     - E: Energy (kg\*U^2/s^2)
     - J: Jerk (U/s^3)
     - M: Mass (kg)
     - N: Unitless
     - R: Resistance (kg/s)
     - W: Weight (for averages)
     - Y: Yank (kg\*U/s^3)
     - Alpha: Acceleration (U/s^2)
     - Gamma: Field (kg/s^2)
     - Theta: Angle (rad)
     - Eta: Number of moles (mol)
     - Mu: Permiance/Molar mass (kg/U)
     - Nu: Frequency (1/U)
     - Xi: Action (kg\*U^2/s)
     - Pi: Change in Volume (U^3/s)
     - Tau: Torque (kg\*U^3/s^2)
     - Upsilon: Main unit (U)
     - Omega: Change in Area (U^2/s)
  - The letters with tilde variants are listed below.
     - \Lms \lms: Returns "B" or "b" with a tilde on it for logarithmic measurements (in dB, for example).
       - Regular B's are the magnetic field/viscosity (kg/U*s).
     - \Freq \freq: Returns "F" or "f" with a tilde on it for frequency. Regular F is force (kg\*U/s^2).
     - \Amom \amom: Returns "L" or "l" with a tilde on it for angular momentum (kg*U^3/s^2). Normal L is length (m).
     - \Mntm \mntm: Returns "P" or "p" with a tilde on it for momentum (kg\*U/s). Normal P is power (kg\*U^2/s^3).
     - \Ht \ht: Returns "Q" or "q" with a tilde on it for heat (J). Regular Q is charge.
     - \Spnt \spnt: Returns "S" or "s" with a tilde on it for the false Poynting Vector (kg/U\*s^3). Normal S is the Poynting Vector (kg^2/U\*s^3).
     - \Temp \temp: Returns "T" or "t" with a tilde on it for temperature (K). Regular T is time (s).
     - \Vol \vol: Returns "V" or "v" with a tilde on it for volume (U^3). Regular V is velocity (U/s).
     - \Eme \eme: Returns capital or lowercase lambda with a tilde on it for EM energy (J). Regular Lambda is light energy (lm\*s)
     - \Snd \snd: Returns capital or lowercase sigma with a tilde on it for loudness (sone)(None-SI). Regular Sigma is sound pressure (Pa)
