
LANGUAGE=en

TARGET=arduino.tex

PREFIX?=.

INSTALL=install

SHAREDPATH=../../shared
TEXFONTS=$(SHAREDPATH)/fonts
TEXINPUTS=$(TEXFONTS):$(SHAREDPATH)/sty

all: arduino

arduino: $(TARGET) $(TARGET:.tex=.gls) 

	TEXFONTS=:$(TEXFONTS) TEXINPUTS=:$(TEXINPUTS) pdflatex $(TARGET)

%.gls: %.tex
	TEXFONTS=:$(TEXFONTS) TEXINPUTS=:$(TEXINPUTS) pdflatex $<
	makeglossaries $(<:.tex=)

install: $(TARGET:.tex=.pdf)
	$(INSTALL) -T --mode=644 $< $(PREFIX)/$(TARGET:.tex=-$(LANGUAGE).pdf) 

clean:
	rm -f *.aux *.log *.snm *.out *.toc *.nav *intermediate *~ *.glo *.glg *.gls *.ist

distclean: clean
	rm -f $(TARGET:.tex=.pdf)
