
INCLUDE_PATH=-I$(TOPDIR)/include -I$(TOPDIR)/src

LIB_PATH = $(TOPDIR)/lib

ifneq ($(URL1), )
INCLUDE_PATH+= -D TEST_URL=\"$(URL1)\"
endif

ifneq ($(URL2), )
INCLUDE_PATH+= -D TEST_URL2=\"$(URL2)\"
endif

ifneq ($(URL3), )
INCLUDE_PATH+= -D TEST_URL3=\"$(URL3)\"
endif

ifneq ($(URL4), )
INCLUDE_PATH+= -D TEST_URL4=\"$(URL4)\"
endif

ifneq ($(AUTH), )
INCLUDE_PATH+= -D TEST_AUTH=\"$(AUTH)\"
endif

CFLAGS = $(INCLUDE_PATH)

LDFLAGS = -L$(LIB_PATH) -lwilddog -lpthread
ifeq ($(COVER), 1)
LDFLAGS+= -lgcov
endif
TARGET=selftest

TEST_SRCS=$(wildcard *.c)
TEST_OBJS=$(patsubst %.c, %, $(TEST_SRCS))



testall:
	@for test_obj in $(TEST_OBJS);\
		do\
			$(CC) $(CFLAGS) -o $$test_obj $$test_obj.c $(LDFLAGS);\
			mv $$test_obj $(TOPDIR)/bin;\
			rm -rf *.d.* *.d;\
		done

include $(TOPDIR)/project/linux/env.mk



		
