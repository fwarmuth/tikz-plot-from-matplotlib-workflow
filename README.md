# tikz-plot-from-matplotlib-workflow
Just some notes and reminders how to get a tikz plot from matplotlib.

## Generate figure, some python Matplotlib snippet:
```
import matplotlib.pyplot as plt
import numpy as np
plt.style.use("ggplot")

t = np.arange(0.0, 2.0, 0.1)
s = np.sin(2 * np.pi * t)
s2 = np.cos(2 * np.pi * t)
plt.plot(t, s, "o-", lw=4.1)
plt.plot(t, s2, "o-", lw=4.1)
plt.xlabel("time (s)")
plt.ylabel("Voltage (mV)")
plt.title("Simple plot $\\frac{\\alpha}{2}$")
plt.grid(True)
```
## Save the figure as a tikz file using parameter for size.
```
from matplotlib2tikz import save as tikz_save
tikz_save('test.tikz',
           figureheight='\\figureheight',
           figurewidth='\\figurewidth'
          )
```
## Prepare the .tex document, import needed packages:
```
\usepackage[utf8]{inputenc}
\usepackage{tikz}
\usepackage{pgfplots}
\pgfplotsset{compat=newest}
\usepgfplotslibrary{groupplots}
\usepgfplotslibrary{dateplot}
```
## Use that .tikz file within Latex, here an example figure:
```
\begin{figure}[h!]
  \caption{Imported as .tikz}
  \centering
  \newlength\figureheight
  \newlength\figurewidth
  \setlength\figureheight{3cm}
  \setlength\figurewidth{3cm}
  \input{test.tikz}
\end{figure}
```
