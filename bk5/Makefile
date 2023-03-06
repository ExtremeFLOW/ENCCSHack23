FCLAGS  = `pkg-config --cflags neko`
LIBS    = `pkg-config --libs neko`
FC      = `pkg-config --variable=compiler neko`
INC_FLAGS = `pkg-config --cflags-only-I neko`

DEST    = bk5
SRC	= ax_bk5.f90 driver.f90
OBJ	= ${SRC:.f90=.o}

all: $(DEST)

install:

clean:
	-rm -f *.o core *.core $(OBJ) $(DEST)

$(DEST): hip ${OBJ}
	$(FC) $(FCLAGS) ax_bk5_aux.o \
		${OBJ} -o $@  $(LIBS)

hip:
	hipcc ${INC_FLAGS} --offload-arch=gfx90a -O3 -c ax_bk5_aux.hip

%.o: %.f90
	${FC} ${FCLAGS} -c $<


