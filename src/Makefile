CC=gcc
CFLAGS=-Wall -Werror
LIB_TARGET=libtadns.so
CLIBFLAGS=-fPIC -shared -Wl,-soname,$(LIB_TARGET).1.0.1
SOURCES=tadns.c
PROGRAM_TARGET=tadns

INSTALL_PREFIX=/usr

all: library program
	@echo "library and program succesfull compiled."

program:
	$(CC) $(CFLAGS) -o $(PROGRAM_TARGET) $(SOURCES) -DADIG

library:
	$(CC) $(CFLAGS) $(CLIBFLAGS) -o $(LIB_TARGET)

install: install_program install_library

install_program:
	cp "$(PROGRAM_TARGET)" "$(INSTALL_PREFIX)/bin"

install_library:
	cp "$(LIB_TARGET)" "$(INSTALL_PREFIX)/lib"
	mkdir -p "$(INSTALL_PREFIX)/include/tadns"
	cp *.h "$(INSTALL_PREFIX)/include/tadns"
	ln -s "$(INSTALL_PREFIX)/lib/$(LIB_TARGET)" "$(INSTALL_PREFIX)/lib/$(LIB_TARGET).1"
	ln -s "$(INSTALL_PREFIX)/lib/$(LIB_TARGET)" "$(INSTALL_PREFIX)/lib/$(LIB_TARGET).1.0"
	ln -s "$(INSTALL_PREFIX)/lib/$(LIB_TARGET)" "$(INSTALL_PREFIX)/lib/$(LIB_TARGET).1.0.0"

uninstall: uninstall_program uninstall_library
	@echo "success"

uninstall_program:
	@echo "uninstalling $(PROGRAM_TARGET) ..."
	rm -f "$(INSTALL_PREFIX)/bin/$(PROGRAM_TARGET)"

uninstall_library:
	@echo "uninstalling $(LIB_TARGET) ..."
	rm -f "$(INSTALL_PREFIX)/lib/$(LIB_TARGET)"
	rm -f "$(INSTALL_PREFIX)/lib/$(LIB_TARGET).1"
	rm -f "$(INSTALL_PREFIX)/lib/$(LIB_TARGET).1.0"
	rm -f "$(INSTALL_PREFIX)/lib/$(LIB_TARGET).1.0.0"

clean:
	@rm -f *.o $(PROGRAM_TARGET) $(LIB_TARGET)
