#	$Id: Makefile 456 2016-03-23 20:06:15Z pwessel $
#
#	makefile for gmtmex/src directory

include ../config.mk

.SUFFIXES:	.m .$(MEX_EXT)

FLAGS		= $(GMT_INC) $(MEX_INC)
ALLLIB     	= $(GMT_LIB) $(MEX_LIB)

PROGS_C		= gmtmex.c
PROGS_O         = $(PROGS_C:.c=.o)
PROGS           = $(PROGS_C:.c=.$(MEX_EXT))
PROGS_H		= gmtmex.h
SCRIPTS         = gmt.m
LIB_C		= gmtmex_parser.c
LIB_O		= $(LIB_C:.c=.o)

#-------------------------------------------------------------------------------
#	software targets
#-------------------------------------------------------------------------------

all:		$(PROGS)

install:	all
		$(INSTALL) -d $(GMT_BIN)
		$(INSTALL) $(PROGS) $(SCRIPTS) $(GMT_BIN)

uninstall:
		cd $(GMT_BIN); rm -f $(PROGS) $(SCRIPTS)

spotless::	clean

clean:	
		rm -f *.o *% core tags gmtmex.mex* gmtmex.oct gmt_opttest

#-------------------------------------------------------------------------------
#	program rules
#-------------------------------------------------------------------------------

gmtmex.$(MEX_EXT):	$(PROGS_O) $(LIB_O)
		$(MEX_BLD) $(FLAGS) $(PROGS_O) $(LIB_O) $(ALLLIB) -o gmtmex.$(MEX_EXT)

.SUFFIXES:	.o .c

.c.o:
		$(CC) $(FLAGS) $(CFLAGS) $(GMT_INC) -c $<
