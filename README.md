# LaTeX thesis template

This is my master thesis template for use at VŠB - Technical University of Ostrava, but you can use it for any university.

## Your information and title page

To change title page, customise text in the brackets located in the `main.tex` file.

```tex
%%%% your information
\university{your university}
\faculty{your faculty}
\department{your department}
\title{Title page}
\titleen{Title page (en)}
\author{your name}
\supervisor{your supervisor}
\city{Ostrava}
\year=2021
```

### Title page

To customise title page go to the `preamble.tex` and scroll down to the bottom of the `.tex` file. There you will find this setup. 

```tex
%%%% titlepage

\renewcommand{\maketitle}{
	\thispagestyle{empty} 
	{\centering
	{\large\scshape
		\@university\\
		\@faculty \\
		\@department
	}
	\vfill
	{
		\LARGE\sffamily{
			{\textbf\@title\\}
			\vspace{1em}
			\@titleen\\
		}
	}
	\vfill
	\begin{tabularx}{.8\textwidth}{XX}
		Autor: & \@author\\
		Vedoucí diplomové práce: & \@supervisor
	\end{tabularx}\\
	\vspace{2em}
	\@city~\the\year\\
}
	\clearpage
}
```

## Structure

I use `subfiles` package for pulling individual `*.tex` files into `main.tex`. Writing is therefore divided into individual chapters, every chapter has its own `.tex` file.

Chapters are printed by `\subfileinclude{}` command. __If you have more chapters, add__ `chapter_08.tex` file into `/chapters/` folder and print it by `\subfileinclude{chapters/chapter_08}` et cetera.

```tex
%%%% chapters
\subfileinclude{chapters/chapter_01}

\subfileinclude{chapters/chapter_02}

\subfileinclude{chapters/chapter_03}

etc....
```

Each subfile has to contain
```tex
\documentclass[main.tex]{subfiles}

\begin{document}
...
\end{document}
```

where `[main.tex]` refers to ROOT file `main.tex` .

You can then write as usual by adding `\section`, `\subsection`, et cetera.

## Typesetting

__LuaLaTeX__ compiler is necessary for this to work.

## Assignment

To upload your assignment, substitute `/config/assignment.pdf` with your `assignment.pdf` file

## Figures

I would recommend you to make subfolder, where you can store all figures. Then you write

```tex
\begin{figure}[H]
  \includegraphics[]{your subfolder/your figure.png}
  \caption{}
\end{figure}
```

I would recommend using argument `[H]` which places the float precisely at the location in the LaTeX code. For more information check: https://en.wikibooks.org/wiki/LaTeX/Floats,_Figures_and_Captions

## Fonts

Big advantage of typesetting with LuaLaTeX is, that you can use any font, that is stored in your computer, __BUT YOU HAVE TO DOWNLOAD THEM__. To change font go into `config/preamble.tex` 

```tex
\usepackage{fontspec} 
\defaultfontfeatures{Ligatures=TeX}
%	\setmainfont{TeXGyreTermes-Regular}[
%		BoldFont       = TeXGyreTermes-Bold ,
%		ItalicFont     = TeXGyreTermes-Italic ,
%		BoldItalicFont = TeXGyreTermes-BoldItalic,
%		NFSSFamily     = ntxtlf]
% 	\setsansfont{TeX Gyre Heros Regular}[
%		Scale=.9,
%		BoldFont       = TeXGyreHeros-Bold,
%		ItalicFont     = TeXGyreHeros-Italic,
%		BoldItalicFont = TeXGyreHeros-BoldItalic]
%	\setmonofont[StylisticSet={1,3},Scale=.9]{inconsolata}
```

If you want your thesis to look great, I would recommend sticking with either _Computer modern_ (used by default) or _TeXGyre_ (like Times/Helvetica). To use _TeXGyre_ delete `%` at the beginning of each line (uncomment).

## Headers/footers

To make headers/footers I use `fancyhdr` package. To customise go to `main.tex`

```
% head/footnote settings for chapters
\pagestyle{fancy}	%makes headers/footers
\fancyhf{}
\rhead{Diplomová práce} %right side headers
\lhead{VŠB -- TUO} %left side headers
\chead{your name} %center headers
\lfoot{Title name} %left side footers
\rfoot{\thepage} %right side footers
\renewcommand{\headrulewidth}{1pt}
\renewcommand{\footrulewidth}{1pt}
```

Headers and footers are used only for chapters/sections.

## Nomenclature

Nomenclature can be done by using commands `\msym` and `\msho` as shown in the template. The commands are defined by:

```tex
\newcommand{\msym}[3]{\noindent\parbox[t]{3cm}{#1}\parbox[t]{9cm}{#2}\hfill\parbox[t]{2cm}{[#3]}\vspace{12pt}} 
\newcommand{\msho}[2]{\parbox[t]{3cm}{#1}\parbox[t]{12cm}{#2}\vspace{12pt}\\}
```


## Bibliography

You can add bibliography into `main.bib` file and print it by `\cite{"key"}` command.

Bibliography style is set to czechinounsrt. For this purpose you will find `czechinounsrt.bst` file in main directory.

More information about bibliography here: https://en.wikibooks.org/wiki/LaTeX/Bibliography_Management

## Useful links

TBD

## Last word

I am open to any ideas, that would improve this template. Hope you will find this template useful.
