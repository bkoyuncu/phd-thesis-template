That line means the following:
If your LaTeX document uses TikZ externalization — a feature that pre-renders TikZ figures into separate PDF files so they don’t have to be redrawn every time you compile — then instead of compiling your .tex file directly with pdflatex or latexmk, you should build your project using the provided Makefile command:
make thesis-force
Breakdown:
	•	“externalize your TikZ figures”:You are using\usetikzlibrary{external}
	•	\tikzexternalize[prefix=figures/]
	•	This tells LaTeX to save each TikZ figure as an external PDF file during the first compilation.
	•	“use the makefile to build”:The Makefile likely automates several compilation steps — including running LaTeX multiple times, handling .aux and .toc files, and regenerating TikZ figures when they change.
	•	make thesis-force:This is probably a Makefile target that forces regeneration of all externalized TikZ figures (e.g., by deleting old ones or forcing re-rendering). It ensures that all figures are up to date before producing the final thesis.pdf.
In short:
When TikZ externalization is enabled, compile your document with make thesis-force instead of pdflatex thesis.tex, because the Makefile properly handles externalized figure rebuilding.
----
