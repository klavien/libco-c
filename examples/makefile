COMM_MAKE = 1
COMM_ECHO = 1
version=0.5
v=debug
include co.mk

########## options ##########
CFLAGS += -g -fno-strict-aliasing -O2 -Wall -export-dynamic \
	-Wall -pipe  -D_GNU_SOURCE -D_REENTRANT -fPIC -Wno-deprecated -m64

UNAME := $(shell uname -s)

ifeq ($(UNAME), FreeBSD)
LINKS += -g -L./lib -lcolib -lpthread
else
LINKS += -g -L./lib -lcolib -lpthread -ldl
endif

#COLIB_OBJS=co_epoll.o co_routine.o co_hook_sys_call.o coctx_swap.o coctx.o co_comm.o
#co_swapcontext.o

#PROGS = example_specific example_closure
PROGS = example_copystack example_setenv example_thread example_cond example_echocli example_echosvr example_poll

all:$(PROGS)

example_echosvr:example_echosvr.o
	$(BUILDEXE) 
example_echocli:example_echocli.o
	$(BUILDEXE) 
example_thread:example_thread.o
	$(BUILDEXE) 
example_poll:example_poll.o
	$(BUILDEXE) 
#example_exit:example_exit.o
#	$(BUILDEXE) 
example_cond:example_cond.o
	$(BUILDEXE)
#example_specific:example_specific.o
#	$(BUILDEXE)
example_copystack:example_copystack.o
	$(BUILDEXE)
example_setenv:example_setenv.o
	$(BUILDEXE)
#example_closure:example_closure.o
#	$(BUILDEXE)

clean:
	$(CLEAN) *.o $(PROGS)

