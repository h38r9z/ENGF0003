java c
CO2   Dissolution in   Water
ENGF0003 Project
24-25
Guidelines:
•       Type   your   project   in   Word   or   LaTeX.   Follow   UCL   Accessibility   Guidelines   to   format   your   document.   Include   a   table   of   contents,   page   numbers,   and   use   built-in styles (Heading   1, Heading 2) to structure your   document.
•       All figures and tables   must   be   numbered and   contain   informative   captions. All   the    main    equations      throughout    your    work    must      be      numbered      and      typed   appropriately.
•       Submit    a    single    PDF      document.      Do      not      write      down    your      name,      student   number,   or   any    information   that   might   help   identify   you   in   any   part   of   the   project.   Do   not   copy   and   paste   the   coursework   brief   into   your   submission   –   Rewrite information where necessary for   the sake of your argument.
This project counts towards 30% of your final   ENGF0003 grade.
Introduction
In your ENGF0003 coursework you have taken a data-driven approach to   studying   ocean acidification   via summarising, describing, visualising   and   generalising data into mathematical   models.
In this   project, you will work with two theoretical   models of the   dissolution   of CO2   in water,   implement   them,   and   discover   how   theory   compliments   real-world   data   in   engineering mathematics.
1.1             Phase   Equilibrium
During   your   ENGF0003   journey,you   have   learned   about   stationary   points, which are those where the derivative of a function is zero and the function does not change   with time. The   mathematical   model   of CO2    equilibrium   in water   is similar, where   we   assume   that   variables   such   as   temperature   and   pressure   do   not   change with   time,   or   change   so   slow   that   we   can   say   that   their time   derivative   is   sufficiently   close   to   zero.
To   create   a   mathematical   model   of the   solubility   of carbon   dioxide   in   seawater,   we   start   from   a   law   of   physics   known   as   Henry’s   Law.   Henry’s   Law   states   that   the   amount of   gas dissolved in a liquid at constant   temperature increases as the pressure   of the gas above the surface of the   liquid   is   raised.
In this project, two main simplifications   will be made to model surface ocean   water,   the real-world system we wish to   model:
i.             We will assume that surface seawater behaves like pure water. This   assumption   is   made   because   there   are   well-documented   empirical   relations   for CO2   dissolution in   pure water.
ii.             Although   the   atmosphere   is   composed   of   H2O   vapour,   N2,   O2   ,   Ar,   CO2   ,   Ne,   He,   CH4   ,   Kr,   H2   ,   NO,   Xe,   O3   ,   I2   ,   CO   and   NH3   ,   we   will   focus   on   modelling   a   system that is formed only   of   H2O   and   CO2   .
1.1.1   Henry’s   Law
Figure   1 shows   a   closed   container with   a gas   and   a   liquid   phase, where the   gas   phase is represented in orange and the liquid phase   is   represented   in   blue.   Suppose   that this system represents a mixture of   water and CO2    both at temperature T   [K] and   total pressure   P    [Pa].
•       In the   gas   phase, there   is   a   mixture   of water vapour and   CO2    gas.
•       In   the    liquid    phase,   there    is   a    mixture   of   liquid   water   and   CO2       particles   dissolved into the water.



Figure   1.   Closed container where a mixture is in phase equilibrium.
Henry’s law states that the   following relations   are   valid in equilibrium (Carey, 1988;   Carroll, Slupsky and   Mather,   1991):
x1   pv,   1      =   y1   φ1   p,                                                                                                                                                                                     (1.1)
x2   H21      =   y2   φ2   p.                                                                                                                                                                                  (1.2)
In equations   1.1 and   1.2 xi       is the   molar fraction of the component with   index   i   in the liquid phase, and yi       is the molar fraction of the same   component   in the vapour   phase. Water is the solvent of   the   system,   being   represented   by   an   index   i    =    1   and   carbon dioxide is the solute represented   by   an   index   i    =   2.
•       We will model the gas phase in terms of the   mass fraction of CO2    in gas   formy2    and   the   mass   fraction   of   water   vapour   y1 .
•       Likewise, we model the   mass fraction   of   water   in   liquid   phase   as   x1      and   the mass fraction of CO2    dissolved in water as x2 .
This results in a   system   of equations   such   as

Finally, Pv,1    is   the   vapour   pressure   of   water   described   empirically   by   Equation   3   and   H21       is   the   temperature-dependent   Henry’s   constant   described   empirically   by   Equation 4.
The coefficients   φ1    and φ2      are the fugacity   ratio   in vapour and   liquid   phases, denoted   as      φ1      =   φl1/φv1   and   φ2      =   φ   .   The fugacity   ratios   allow   us   to   approximate   non-ideal       gases       more       accurately       while       using       idealised       equations.       Appendix       A   summarises the approach of Peng and Robinson (1976) in   obtaining these quantities.
1.1.2   Vapour   Pressure of Water
The   vapour   pressure   of   water   is   represented   as   Pv,1 .   This   quantity   can   be   computed with the empirical approximation given by the   International Association for   the   Properties of Water and Steam   IAPWS   (Wagner and   Pruß, 2002) as

where   x   =   1   −   Tr ,   and   Tr      =   T/Tc             is    a    non-dimensional    temperature   variable    and   values for αi      in Eq. 3 can be found in Table   1.   In   Eq. 3,   Tc       =   647.096   [K]   is the critical   temperature of water, and Pc       =   22.064   [MPa] is the critical pressure   of   water.
Table   1. Coefficients αi    for   Equation   3

1.1.3   Henry’s Constant
H21    is the Henry constant for the system H2O + CO2   .   An empirical temperature-   dependent expression for H21 (T)   is given by (Carroll, Slupsky and   Mather,   1991)   as

where the coefficients ℎ   i      can be   found   in   Table   2.
Table 2. Coefficients ℎ   i      for   Equation 4.





1.2                Reaction   Kinetics
When   considering   engineering   mathematical   models,   we   need   to   pay   close   attention to time scales. This   means that some   parts   of   our   problem   might   be   better   represented   as   stationary   phenomena,   like   in   1.1,   but   other   parts   of   happen faster,   and it is important to   understand   how   they   develop   in   time.
We will   now explore a time-dependent model   of the solubility   of   CO2    i代 写ENGF0003 CO2 Dissolution in Water 24-25Matlab
代做程序编程语言n water.   In    specific,    we   will    focus    on    mathematical    models    of    the    cascade    of    chemical   reactions triggered when CO2    is dissolved in water.
Carbon   dioxide   does   not stay   inert when   it   dissolves   in water.   It   undergoes   a   chain of reversible chemical reactions producing carbonic   acid   (H2   CO3   ),   bicarbonate   ion (HCO3(−)), carbonate ion   (CO3(2)   −   ) and   hydrogen   ion   (H+   ).
This chain   is expressed through   Reactions   1 – 4 as:

The kinetics of these   reactions can be   modelled by a   system   of   nonlinear   ordinary differential equations given by:


In these equations,   t   is time in seconds   and a square bracket around the name of   a   chemical   species   indicates   its   concentration.   ki       represents   rate   constants   for the   ith   reaction. Since these   reactions are   reversible,   ki       denotes a forward   rate and   k   −i   a   reverse   rate.
The    rate    constants    ki          and    k   −i          are    given    in    inverse    second    [s-1].    The    set    of   equations 5.1 – 5.6 can   be   interpreted as   follows:
•       Eq.   5.1   models   R1   and   accounts for   the   time   it   takes   for   carbon   dioxide   gas,   represented as   CO2 (g) to dissolve into water and become   aqueous   CO2 (aq).
•         Eq. 5.2   models both   R1 and   R2.   It   accounts   for:
o   Production of CO2 (aq)   by the dissolution of CO2 (g)   at   rate   k1 ,
o   Loss of CO2 (aq)   by reverse   reactions back to   CO2 (g)   with   rate   k   −1 ,
o   Loss/production of CO2 (aq)   by forward/reverse   reactions to/from   H2   CO3 .
A similar logic can be used for   Eqs.   5.3 –   5.6.   The   concentrations   in   Eqs.   5.1   –      5.6 are given in molarity   [M] which is   equivalent to   one   mol   of the   chemical   species   per litre of water. The best case-study to understand the   dynamics   of   CO2   dissolution in water is to imagine a system where   all   species   are   in   equilibrium   at   t   =   0. Table 3 shows the equilibrium molarities for all species   in this   reaction.
Table 3. Forward and   reverse   rate   constants.





If   at   t   =   0   we   inject   gaseous   carbon   dioxide   at   concentration   [CO2 (g)]0      =   0.065   [M], this will   trigger a   cascade   of   reactions that   will   cause   all   other   species   to   react   and then reach equilibrium within   100 seconds.
The   equilibrium   conditions   in   [M]   for   all   species   which   should   be   used   as   initial   conditions in solving this system of differential equations at 25˚C and   1   atm pressure   are:
[CO2 (aq)]0      =   5.41   ×   10   −4
[H2   CO3   ]0      =   1.64      ×   10   −6
[HCO3(−)]0      =   3.28   ×   10   −4




[CO3(2)   −   ]0      =   1.97   ×   10   −8
[H+]0      =   1   ×   10   −6
Implementation tips:
•       Use    the    self-paced    course Solving    Ordinary    Differential    Equations      with   MATLAB   to   learn   how   to   write   solutions   to   systems   of   non-linear   ODEs   in MATLAB.
•       Since the scales of the rate   parameters   in   Table   3 vary widely   from   10   −2      to   1010   ,   the   best   MATLAB   solvers   for   this   system   are   stiff   solvers   such   as   ode15s   or   ode23s.
•       You   are   also   recommended   to   set   an   Absolute   Tolerance   ‘AbsTol’   of   10   −12   and   Relative Tolerance ‘RelTol’ of   10   −6    for this   problem   because the   initial   conditions are as low as   10   −8      and   might   get smaller.
[40 marks]   Task   1
Your task is to study, describe, and operationalise the mathematical model in section   1.1 of this document.       [3   PAGE   MAXIMUM]
A.   Mathematical   Task:    Express    Eqs.    1.1,    1.2,    2.1,    and    2.2   as   a   linear   system in terms of matrix-vector multiplication and matrix   inversion.   Find   the   conditions   where   the   model   represented   by   Eqs.   1.1,   1.2,   2.1,   and   2.2 cannot   be solved.   Discuss the   implications of this condition   in a   real-   life system.
B.   Communication   Task:   Create   a   schematic   showing   how   all   equations   in Appendix A and   pages 4 through to 8 in this   brief are   connected. Your   summary should communicate clearly how they can be solved in a logical   order.   Use   this   schematic   to   describe   how   you   will   structure   MATLAB   code to solve this   problem.
C.   Modelling Task: Propose an extended version of   the model in Equations   1.1 through to 2.2 that also   includes gases other than CO2   .   Describe   the   specific   quantities   that   you   would   need   before   implementing   this   model   computationally.
[30 marks]   Task   2
Your task is to implement and validate the   mathematical   model   in   1.1   in   MATLAB.       [2   PAGE   MAXIMUM]
A.   Coding   Task:   Use   MATLAB   to   calculate   and   plot   H21   ,   Pv,1 ,   φ1      and   φ2   when   T   ∈   [10, 80]    ˚C   and   P   =   101.325   kPa.   Use   the   subplot   function   to   produce a 2x2   grid   of figures.
B.   Validation   Task: Use MATLAB   to calculate the equilibrium concentration   of   CO2      in   water   x2 (T, P)   for   T   ∈   [10, 80]    ˚C   and   four   distinct   pressures   such that P   ∈   {50, 101.325, 200}   kPa. Contrast and compare your   results   with those of Table 3   in   (Carroll, Slupsky   and   Mather,   1991)   .
C.   Modelling Task: Attached to this brief is a comprehensive dataset of the   Great       Barrier       Reef.       Use       data      on       pressure,      temperature      and      air   concentration   of   CO2    to   model   the   equilibrium   concentration   of   CO2      in   water   over   time.
[30 marks]   Task   3
Your task is to study, describe, and operationalise the mathematical model in section 1.2 of this document.      [2   PAGE   MAXIMUM]
A.   Coding   Task:   Use   MATLAB   to   solve the   system   of ordinary   differential   equations shown in   Eqs. 5.1 – 5.6 using the reaction   rates given   in Table   3 and the initial conditions outlined   in page   11.   Plot your time-dependent   solutions for all chemical species   in a   single   figure.
B.   Analysis   Task:   Contrast   and   compare   the   speed   at   which   each   of the   reactions   in   page   9   takes   place.   Use   the   constants   in   Table   3   and   your   numerical   solution   of   the   system   5.1   –   5.6   to   support   your   argument.   Estimate    the    time    it    takes    for    the    full    system    to    reach    steady-state   equilibrium.
C. Summary    Task:    Contrast    and      compare      the      Phase      Equilibrium      and   Reaction   Kinetics   models   in   this   project.   Explain what   phenomena   they   represent    and    how    these    are    connected.      Discuss    their    fundamental   assumptions       and       how       these       assumptions    shape and    limit    their   possibilities.

   

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
