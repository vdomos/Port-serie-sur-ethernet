all: remserial

REMOBJ=remserial.o stty.o
remserial: $(REMOBJ)
	$(CC) $(LDFLAGS) -o remserial $(REMOBJ)

install:
	sudo cp remserial /usr/local/bin
clean:
	rm -f remserial *.o
