---
layout: post
title: "tutorials_latex"
date: 1970-01-01
---

====== TikZ ======

Font typefaces: 

Computer Modern, Latin Modern, Post script Fonts, Tex Gyre.

Fonts families:

rmdefault, sfdefault, ttdefault

Font sizes:

tiny, large, huge

Fonts styles:

textmd, textbf, textup, textit, textsl, textsc




When you specify a coordinate like for a rectangle or a circle with

   \draw or \filldraw (0,0) rectangle +(1,2)

the coordinates are converted later during the transformation.

The general syntax is 
    
    \foreach <variable> in {<list of values>} <commands>.


\usepackage{layouts}

\usepackage[showframe]{geometry}

\pagediagram

\printinunitsof{mm}{\pagevalues}

\verb|\marginparwidth|: \printinunitsof{mm}\prntlen{\marginparwidth}

pdflatex -aux-directory=DIR -output-directory=DIR filename.tex
mktexmf
\include{subfile}  – this is like a include. Plugins : scrbook.cls beamer.cls everyshi.sty  natbib, nhchem, sectsty, preprint, lastpage, caption, fancyhdr, symbol,

Because I hate the  mouse and almost like to do everything from the command line, I find  latex great. I found a website called sharelatex and one can make  private projects and the website will compile it for you. Still, I have  locally installed latex using texlive-full. All the packages has been  downloaded and installed and one can check this using the command  dpkg-query -l | grep texlive.
I am currently trying to understand  how the table works and have started with the basic tabular package.  cline{2-2} , multicol{3}[c}[text}, multirow{3}{*}{text},  \begin{tabular}{center}{|clp{10cm}|} are some of the basics that I need  to remember by heart.


\begin{itemize}
\item
\end{itemize}


\usepackage{url}
\url

\usepackage{datetime}
\displaydate

display math  in $$ .... $$
textmath $  ... $

Two kind of commands: 
control commands are of two types : control symbols and control words.


Commands followed by argeuments
'\vskip 2in' where 2in is the arguement

Commands followed by parameters
\vskip\parskip

\null doesnt produce any output

\thinspace is to provide a small space between two words. This is lesser than a normal space.

Always use single quotes or two single quotes to show a double quote.

Special characters and should be delimited with a backslash
\$ \_ etc.

Groups:

\bf{a few boldface words}
If you write \bf a few boldface word... Then everything after \bf is boldface

similarly \parident=15pt{begin paragraph} idents only those paragraphs to 15pt where this is written.

\parskip, \noident, \vskip, \smallskip, \leftskip, \rightskip, \narrower, 
always end with \par}

A paragraph in latex starts default at 0.25in


pdflatex -aux-directory=DIR -output-directory=DIR filename.tex
mktexmf
\include{subfile}  – this is like a include. Plugins : scrbook.cls beamer.cls everyshi.sty  natbib, nhchem, sectsty, preprint, lastpage, caption, fancyhdr, symbol,
Linux Admin
p  in sed is very powerful because it prints the name of the original and  the name of the changed thing. This can be then piped to xargs with -n2  i.e sed ‘p;s/pattern/replacement’ | xargs -n2 mv Ofocurse the sed  command itself has to have an input and this comes from another pipe  such as ls | sed or echo “dfds” | sed
su – password
chmod +t /usr/local/tmp or chmod 1777 /usr/local/tmp
diff -rq directory1 directory2 | sort | less
diff -iBc file1 file2
tar -xvjf tar -xvzf tar -cvzf directory


Because I hate the  mouse and almost like to do everything from the command line, I find  latex great. I found a website called sharelatex and one can make  private projects and the website will compile it for you. Still, I have  locally installed latex using texlive-full. All the packages has been  downloaded and installed and one can check this using the command  dpkg-query -l | grep texlive.
I am currently trying to understand  how the table works and have started with the basic tabular package.  cline{2-2} , multicol{3}[c}[text}, multirow{3}{*}{text},  \begin{tabular}{center}{|clp{10cm}|} are some of the basics that I need  to remember by heart.



