CC = gcc
CFLAGS = -Wall -Wno-unused-variable -I../include

LIBKIRK = ../include/libkirk

BINDIR = ../bin
OBJDIR = ../obj

ifeq ($(DEBUG), 1)
CFLAGS+=-g -O0
else
CFLAGS+=-O2
endif

TARGET1 = $(LIBKIRK)/libkirk.a
OBJS1 = $(LIBKIRK)/kirk_engine.o $(LIBKIRK)/aes.o $(LIBKIRK)/des.o $(LIBKIRK)/sha1.o $(LIBKIRK)/amctrl.o $(LIBKIRK)/bn.o $(LIBKIRK)/ec.o

TARGET2 = $(BINDIR)/psxtract
OBJS2 = psxtract.o cdrom.o crypto.o lz.o utils.o

all: $(TARGET1)

$(TARGET1): $(OBJS1)
	$(AR) rcs $@ $(OBJS1)

all: $(TARGET2)

$(TARGET2): $(OBJS2)
	$(CC) $(CFLAGS) -o $@ $(OBJS2) -L $(LIBKIRK) -lkirk


clean:
	rm -rf *.o $(LIBKIRK)/*.o $(TARGET1) $(TARGET2)
