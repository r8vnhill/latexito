# LaTeXiTo
For now I'm just gonna include the code in the README.

## Simple header
```latex
% | Creates a mini-page with a logo to be included in the header/cover.
% | Arguments:
% |   #1 - Path to the logo location
\newcommand{\includeLogo}[1]{
  \begin{minipage}{0.39\textwidth}
    \includegraphics[height=2cm]{#1}
  \end{minipage}
}

% | Creates a mini-page to be included in the header/cover of a university assignment.
% | Arguments:
% |   #1 - Course ID
% |   #2 - Course name
% |   #3 - City
% |   #4 - Country
\newcommand{\includeMetadata}[4]{
  \begin{minipage}{0.59\textwidth}
    \begin{flushright}
      \textsc{#1\ - #2} \\
      \today \\
      \small{\textit{#3, #4}}
    \end{flushright}
    \vspace{-0.45cm}
  \end{minipage}
}

% | Renders a header for a university assignment with the document's metadata.
% | Arguments:
% |   #1 - Path to the logo location
% |   #2 - Course ID
% |   #3 - Course name
% |   #4 - City
% |   #5 - Country
\newcommand{\renderHeader}[5]{
  \includeLogo{#1}
  \hfill
  \includeMetadata{#2}{#3}{#4}{#5}
  \\[2ex]
  \rule{\linewidth}{0.2 mm}
}
```
### Usage:
```latex
\newcommand{\courseID}{CC5502}
\newcommand{\courseName}{Geometría computacional}
\newcommand{\logo}{LogoDCC.pdf}
\newcommand{\city}{Santiago}
\newcommand{\country}{Chile}

\begin{document}
  \renderHeader{\logo}{\courseID}{\courseName}{\city}{\country}
  ...
\end{document}
```

![](https://i.imgur.com/eo7MVU9.png)

## Title with optional subtitle
```latex
% | The package’s basic command is \ifthenelse, which can use a wide array of tests. Also provided 
% | is a simple loop command \whiledo.
% | Ifthen is a separate package within the LATEX distribution; while it will always be present in a
% | LATEX distribution, a \usepackage command is always needed to load it.
\usepackage{ifthen}

% | Renders the document title with an optional subtitle
% | Arguments:
% |   #1 (optional) - The document's subtitle
% |   #2 - The document's title
\newcommand{\renderTitle}[2][]{
  % The notation [2][] indicates that this command receives 2 arguments, the first one being 
  % optional taking the [] (empty) value as default.
  {\Large
    \textbf{#2} \\
    \ifthenelse{\equal{#1}{}}{
      % No subtitle given
      \vspace{4pt}
    }{
      \textit{#1} \\
    }
  }
}
```
### Usage
```latex
%% Reference to the title of the document
\makeatletter
\let\docTitle\@title
\makeatother

\title{Lectura 2}
\newcommand{\docSubtitle}{Towards A Discipline Of Experimental Algorithmics}

\begin{document}
  \renderTitle[\docSubtitle]{\docTitle}
\end{document}
```
