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

\renderHeader{\logo}{\courseID}{\courseName}{\city}{\country}
```

![](https://i.imgur.com/eo7MVU9.png)
