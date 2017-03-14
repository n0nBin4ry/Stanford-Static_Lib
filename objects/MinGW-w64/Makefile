#Recipe to make static library StanLib.a from all the object files
SOURCE = \
	base64.o basicgraph.o bitstream.o \
	call_stack_gcc.o call_stack_windows.o console.o \
	dawglexicon.o direction.o \
	error.o exceptions.o \
	filelib.o \
	gbufferedimage.o gevents.o gfilechooser.o ginteractors.o gmath.o gobjects.o goptionpane.o gtable.o gtextarea.o gtimer.o gtypes.o gwindow.o \
	hashcode.o \
	lexicon.o \
	note.o \
	observable.o \
	plainconsole.o platform.o point.o random.o recursion.o regexpr.o \
	server.o shuffle.o simpio.o sound.o strlib.o \
	timer.o tokenscanner.o \
	urlstream.o \
	version.o
	
TARGET = libStanford64.a

all:
	ar rvs $(TARGET) $(SOURCE)