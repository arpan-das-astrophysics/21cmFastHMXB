# C compiler and flags
CPPFLAGS = -I/usr/local/include
LDFLAGS = -L/usr/local/lib -lgsl -lgslcblas -lfftw3f_omp -lfftw3f -lm
CC      = gcc -fopenmp
#CC      = gcc -fopenmp -mtune=core2 -march=core2 -m64 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_THREAD_SAFE #for my mac pro 64bit


# Directory hosting the non-project specific code
COSMO_DIR = ../Cosmo_c_files

# Directory containing parameter files, definint relevant constants
PARAMETER_DIR = ../Parameter_files

# non-project dependencies
COSMO_FILES = 	${PARAMETER_DIR}/COSMOLOGY.H \
	${COSMO_DIR}/ps.c \
	${COSMO_DIR}/cosmo_progs.c \
	${COSMO_DIR}/misc.c \
	${PARAMETER_DIR}/INIT_PARAMS.H \
	${PARAMETER_DIR}/ANAL_PARAMS.H \
	${PARAMETER_DIR}/HEAT_PARAMS.H \

# object files
OBJ_FILES = init \
	redshift_interpolate_boxes \
	print_power_spec_ICs \
	delta_ps \
	delta_T \
	find_HII_bubbles \
	gen_size_distr \
	perturb_field \
	filter_den_hist \
	boxcar_smooth_field \
	Ts \
	drive_zscroll_noTs \
	drive_zscroll_reion_param \
	drive_xHIscroll
#########################################################################

drive_logZscroll_Ts: drive_logZscroll_Ts.c \
	bubble_helper_progs.c \
	${OBJ_FILES} \
	${COSMO_FILES} \

	${CC} ${CPPFLAGS} -o drive_logZscroll_Ts drive_logZscroll_Ts.c ${LDFLAGS} 


redshift_interpolate_boxes:     redshift_interpolate_boxes.c \
	${COSMO_FILES} \
	filter.c \

	${CC} ${CPPFLAGS} -o redshift_interpolate_boxes redshift_interpolate_boxes.c ${LDFLAGS}


drive_zscroll_noTs: drive_zscroll_noTs.c \
	${COSMO_FILES} \

	${CC} ${CPPFLAGS} -o drive_zscroll_noTs drive_zscroll_noTs.c ${LDFLAGS}


drive_zscroll_reion_param: drive_zscroll_reion_param.c \
	${COSMO_FILES} \

	${CC} ${CPPFLAGS} -o drive_zscroll_reion_param drive_zscroll_reion_param.c ${LDFLAGS}


drive_xHIscroll: drive_xHIscroll.c \
	${COSMO_FILES} \

	${CC} ${CPPFLAGS} -o drive_xHIscroll drive_xHIscroll.c ${LDFLAGS}


init:	init.c \
	filter.c \
	${COSMO_FILES}

	${CC} ${CPPFLAGS} -o init init.c ${LDFLAGS}


print_power_spec_ICs:	print_power_spec_ICs.c \
	${COSMO_FILES}

	${CC} ${CPPFLAGS} -o print_power_spec_ICs print_power_spec_ICs.c ${LDFLAGS}


Ts:     Ts.c \
	${COSMO_FILES} \
	filter.c \
	heating_helper_progs.c \
	elec_interp.c \

	${CC} ${CPPFLAGS} -o Ts Ts.c ${LDFLAGS}


boxcar_smooth_field:       boxcar_smooth_field.c \
	${COSMO_FILES}

	${CC} ${CPPFLAGS} -o boxcar_smooth_field boxcar_smooth_field.c ${LDFLAGS}


filter_den_hist:       filter_den_hist.c \
	${COSMO_FILES} \
	filter.c

	${CC} ${CPPFLAGS} -o filter_den_hist filter_den_hist.c ${LDFLAGS}


perturb_field:	perturb_field.c \
	${COSMO_FILES}

	${CC} ${CPPFLAGS} -o perturb_field perturb_field.c ${LDFLAGS}


gen_size_distr:	gen_size_distr.c \
	${COSMO_FILES}

	${CC} ${CPPFLAGS} -o gen_size_distr gen_size_distr.c ${LDFLAGS} 


delta_ps:	delta_ps.c \
	${COSMO_FILES}

	${CC} ${CPPFLAGS} -o delta_ps delta_ps.c ${LDFLAGS}


delta_T:	delta_T.c \
	${COSMO_FILES}

	${CC} ${CPPFLAGS} -o delta_T delta_T.c ${LDFLAGS}


find_HII_bubbles:	find_HII_bubbles.c \
	bubble_helper_progs.c \
	${COSMO_FILES}

	${CC} ${CPPFLAGS} -o find_HII_bubbles find_HII_bubbles.c ${LDFLAGS}


clean:
	rm drive_logZscroll_Ts ${OBJ_FILES} *~
