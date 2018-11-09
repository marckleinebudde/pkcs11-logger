# Display exported symbols:
#  nm -D pkcs11-logger.so | grep ' T '

CFLAGS += -Wall -Wextra -O2 -fPIC -ggdb
CPPFLAGS += -I.
LIBNAME = pkcs11-logger.so
LDADD = -ldl -lpthread

all: $(LIBNAME)

$(LIBNAME): init.o lock.o log.o pkcs11-logger.o translate.o utils.o
	$(CC) $(ARCH_FLAGS) -shared -o $(LIBNAME) \
	-Wl,-soname,$(LIBNAME) \
	-Wl,--version-script,pkcs11-logger.version \
	$^

%.o: %.c $(wildcard *.h)

clean:
	-rm -f *.o

distclean: clean
	-rm -f *.so
