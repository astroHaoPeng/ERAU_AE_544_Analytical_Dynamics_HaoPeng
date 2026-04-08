% This file include all LaTeX commands used in this Obsidian vault. 
% This file is loaded by the Obsidian plugin `Extended MathJax`.
% This file cannot include non-latex syntax contents, so it has to be excluded from the Obsidian `Linter` plugin.

\newcommand{\bm}[1]{\boldsymbol{#1}}
\newcommand{\ccancel}[2][red]{{\color{#1}\cancel{\color{black}#2}}}
\newcommand{\ccancelto}[3][red]{{\color{#1}\cancelto{#2}{\color{black}#3}}}

\newcommand{\aht}[1]{\hat{\bm{a}}_{#1}}
\newcommand{\bht}[1]{\hat{\bm{b}}_{#1}}
\newcommand{\cht}[1]{\hat{\bm{c}}_{#1}}
\newcommand{\dht}[1]{\hat{\bm{d}}_{#1}}
\newcommand{\eht}[1]{\hat{\bm{e}}_{#1}}
\newcommand{\fht}[1]{\hat{\bm{f}}_{#1}}
\newcommand{\ght}[1]{\hat{\bm{g}}_{#1}}
\newcommand{\iht}[1]{\hat{\bm{i}}_{#1}}
\newcommand{\jht}[1]{\hat{\bm{j}}_{#1}}
\newcommand{\mht}[1]{\hat{\bm{m}}_{#1}}
\newcommand{\nht}[1]{\hat{\bm{n}}_{#1}}
\newcommand{\rht}[1]{\hat{\bm{r}}_{#1}}
\newcommand{\sht}[1]{\hat{\bm{s}}_{#1}}
\newcommand{\uht}[1]{\hat{\bm{u}}_{#1}}
\newcommand{\vht}[1]{\hat{\bm{v}}_{#1}}
\newcommand{\wht}[1]{\hat{\bm{w}}_{#1}}

% Letters wrapped in `\bm{}`
% UPPER CASE
\newcommand{\bmF}{\bm{F}}
\newcommand{\bmG}{\bm{G}}
\newcommand{\bmH}{\bm{H}}
\newcommand{\bmL}{\bm{L}}
\newcommand{\bmQ}{\bm{Q}}
\newcommand{\bmR}{\bm{R}}
\newcommand{\bmV}{\bm{V}}
\newcommand{\bmX}{\bm{X}}
% lower case
\newcommand{\bme}{\bm{e}}
\newcommand{\bmf}{\bm{f}}
\newcommand{\bmg}{\bm{g}}
\newcommand{\bmp}{\bm{p}}
\newcommand{\bmq}{\bm{q}}
\newcommand{\bmr}{\bm{r}}
\newcommand{\bmu}{\bm{u}}
\newcommand{\bmv}{\bm{v}}
\newcommand{\bmw}{\bm{w}}
\newcommand{\bmx}{\bm{x}}
% Greek
\newcommand{\bmbet}{\bm{\beta}}
\newcommand{\bmsig}{\bm{\sigma}}
\newcommand{\bmo}{\bm{\omega}}
\newcommand{\bmO}{\bm{\Omega}}

\newcommand{\Acal}{\mathcal{A}}
\newcommand{\Bcal}{\mathcal{B}}
\newcommand{\Ecal}{\mathcal{E}}
\newcommand{\Ncal}{\mathcal{N}}
\newcommand{\calA}{\mathcal{A}}
\newcommand{\calB}{\mathcal{B}}
\newcommand{\calC}{\mathcal{C}}
\newcommand{\calD}{\mathcal{D}}
\newcommand{\calE}{\mathcal{E}}
\newcommand{\calF}{\mathcal{F}}
\newcommand{\calG}{\mathcal{G}}
\newcommand{\calH}{\mathcal{H}}
\newcommand{\calI}{\mathcal{I}}
\newcommand{\calJ}{\mathcal{J}}
\newcommand{\calL}{\mathcal{L}}
\newcommand{\calM}{\mathcal{M}}
\newcommand{\calN}{\mathcal{N}}
\newcommand{\calQ}{\mathcal{Q}}
\newcommand{\calR}{\mathcal{R}}
\newcommand{\calS}{\mathcal{S}}
\newcommand{\calW}{\mathcal{W}}

\newcommand{\bbR}{\mathbb{R}}

\newcommand{\fkR}{\mathfrak{R}}

% derivatives
\newcommand{\dt}{{\rm d}t}
\newcommand{\dm}{{\rm d}m}
\newcommand{\dx}{{\rm d}x}
\newcommand{\dy}{{\rm d}y}
\newcommand{\dz}{{\rm d}z}
\newcommand{\ddt}[1][]{\frac{{\rm d} #1}{{\rm d}t}}
\newcommand{\dq}{\dot{q}}
\newcommand{\dp}{\dot{p}}

% derivatives in different frame: d( )/dt in any frame
\newcommand{\ddtDoNotUse}[1]{\frac{^{#1}\rm d \phantom{t}}{\phantom{^{#1}}{\rm d }t}}
\newcommand{\ddtA}{\ddtDoNotUse{\calA}}
\newcommand{\ddtB}{\ddtDoNotUse{\calB}}
\newcommand{\ddtD}{\ddtDoNotUse{\calD}}
\newcommand{\ddtE}{\ddtDoNotUse{\calE}}
\newcommand{\ddtF}{\ddtDoNotUse{\calF}}
\newcommand{\ddtG}{\ddtDoNotUse{\calG}}
\newcommand{\ddtM}{\ddtDoNotUse{\calM}}
\newcommand{\ddtN}{\ddtDoNotUse{\calN}}
\newcommand{\ddtS}{\ddtDoNotUse{\calS}}
\newcommand{\ddtW}{\ddtDoNotUse{\calW}}

% 2nd order derivatives in different frames: d^2( )/dt^2 in any frame
\newcommand{\dddttDoNotUse}[1]{\frac{^{#1}{\rm d}^2 \phantom{t^2}}{\phantom{^{#1}}{\rm d}t^2}}
\newcommand{\dddttA}{\dddttDoNotUse{\calA}}
\newcommand{\dddttB}{\dddttDoNotUse{\calB}}
\newcommand{\dddttN}{\dddttDoNotUse{\calN}}

% partial derivatives
\newcommand{\pp}[2]{\frac{\partial #1}{\partial #2}}
\newcommand{\qq}[1]{\left[ #1 \right]_{\bmq, \dot{\bmq}}}
\newcommand{\qp}[1]{\left[ #1 \right]_{\bmq, \bmp}}
\newcommand{\ppqdq}[2]{\left[ \pp{#1}{#2} \right]_{\bmq,\dot{\bmq}}}
\newcommand{\ppqp}[2]{\left[ \pp{#1}{#2} \right]_{\bmq,\bmp}}

% Lagrangian mechanics
\newcommand{\qOneToEnd}[1][n]{q_1,q_2,\dots,q_{#1}}
\newcommand{\qDotOneToEnd}[1][n]{\dot{q}_1,\dot{q}_2,\dots,\dot{q}_{#1}}
\newcommand{\oneTo}[1]{1,2,\dots,{#1}}
\newcommand{\frTwo}{\frac{1}{2}}
\newcommand{\frFour}{\frac{1}{4}}

\newcommand{\col}[1]{\begin{pmatrix}#1\end{pmatrix}}

%%%%%%%%%%%%%%%
% matrix related definitions
%%%%%%%%%%%%%%%
% different matrix brackets
\newcommand{\bmt}[1]{\begin{bmatrix}#1\end{bmatrix}}
\newcommand{\Bmt}[1]{\begin{Bmatrix}#1\end{Bmatrix}}
% common operators
\newcommand{\inv}{^{-1}}
\newcommand{\trans}{^T}
% skew-symmetric tilde operator
\newcommand{\skewmtThree}[3]{\bmt{0 & -#3 & #2 \\ #3 & 0 & -#1 \\ -#2 & #1 & 0}}
\newcommand{\skewmt}[1]{\bmt{0 & -{#1}_3 & {#1}_2 \\ {#1}_3 & 0 & -{#1}_1 \\ -{#1}_2 & {#1}_1 & 0}}
% diagonal matrix
\newcommand{\diagmt}[3]{\bmt{#1 & 0 & 0 \\ 0 & #2 & 0 \\ 0 & 0 & #3}}
% DCM
\newcommand{\dcm}[1]{\left[#1\right]}
\newcommand{\dcmExpand}[1]{\bmt{#1_{11} & #1_{12} & #1_{13} \\ #1_{21} & #1_{22} & #1_{23} \\ #1_{31} & #1_{32} & #1_{33}}}

% Define elementary rotation matrix M1, M2, and M3 introduced in Ch03
\newcommand{\dcmOne}[1]{\bmt{1 & 0 & 0 \\ 0 & \cos #1 & \sin #1 \\ 0 & -\sin #1 & \cos #1}}
\newcommand{\dcmTwo}[1]{\bmt{\cos #1 & 0 & -\sin #1 \\ 0 & 1 & 0 \\ \sin #1 & 0 & \cos #1}}
\newcommand{\dcmThree}[1]{\bmt{\cos #1 & \sin #1 & 0 \\ -\sin #1 & \cos #1 & 0 \\ 0 & 0 & 1}}




% cdFrameates in frame XX
\newcommand{\cdFrame}[2]{\prescript{#1}{}{#2}}
\newcommand{\cdA}[1]{\cdFrame{\calA}{#1}}
\newcommand{\cdB}[1]{\cdFrame{\calB}{#1}}
\newcommand{\cdE}[1]{\cdFrame{\calE}{#1}}
\newcommand{\cdF}[1]{\cdFrame{\calF}{#1}}
\newcommand{\cdG}[1]{\cdFrame{\calG}{#1}}
\newcommand{\cdN}[1]{\cdFrame{\calN}{#1}}
\newcommand{\cdS}[1]{\cdFrame{\calS}{#1}}


% Showing frame for coordinates in bottom right corner.
%   mainly used in Ch01
\newcommand{\cood}[2]{\left( #1 \right)_{#2}}
