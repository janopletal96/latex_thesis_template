# Latex thesis template

This is my master thesis template for use at VŠB - Technical University of Ostrava, but you can really use it for any university.

## Your information

To change titlepage, just customize text in the brackets.

```tex
%%%% your information
\university{your university}
\faculty{your faculty}
\department{your department}
\title{Název práce}
\titleen{Title Page}
\author{your name}
\supervisor{your supervisor}
\city{Ostrava}
\year=2021
```

## Structure

I use `subfiles` package for pulling individual `*.tex` files into `main.tex`. Writing is therefore divided into individual chapters, every chapter has its own `.tex` file.

Chapters are printed by `\subfileinclude{}` command. __If you have more chapters just add__ `chapter_08.tex` file into `/chapters/` folder and print it by `\subfileinclude{kapitoly/kapitola_08}` and so on.
```tex
%%%% chapters
\subfileinclude{chapters/chapter_01}

\subfileinclude{chapters/chapter_02}

\subfileinclude{chapters/chapter_03}

....
```

Each subfile has to contain, where `[main.tex]` refers to ROOT file `main.tex` 
```tex
\documentclass[main.tex]{subfiles}

\begin{document}
...
\end{document}
```
You can then write as usual by adding `\section`, `\subsection`, etc.

## Typesetting

__LuaLaTeX__ compiler is nessesary for this to work.

## Assignment

To upload your assignment, just substitute `/config/assignment.pdf` with your `assignment.pdf` file

## Bibliography

You can add bibliography into `main.bib` file and print it by `\cite{"key"}` command.

Bibliography style is set to czechinounsrt. For this purposu you will find `czechinounsrt.bst` file in main directory.

More information about bibliography here: https://en.wikibooks.org/wiki/LaTeX/Bibliography_Management
