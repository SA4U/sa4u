# INSTALL

## SA4U

### 1. Build the SA4U Docker Image

```sh
# From the root of this directory.
$ cd sa4u_z3/
$ docker image build -t sa4u_z3 .
```

### 2. Verify Installation of SA4U

Test that the image is working on one of SA4U's demo files:

```sh
# From the root of this directory.
$ docker container run             \
    --rm                           \
    -ti                            \
    -v "$(pwd)"/demos/01/:/src/    \
    sa4u_z3                        \
    -p /src/ex_prior.json          \
    -m /src/CMASI.xml              \
    -c /src/
```

You should see this message at the bottom of the tool's output:

```
...
ERROR!
  afrl::cmasi::Location3D::getAltitude return unit known from CMASI definition
  afrl::cmasi::Location3D::getAltitude known from CMASI definition
  Variable z declared in /src/ex.cpp on line 25 (1)
  Call to set_alt_in_cm in /src/ex.cpp on line 31 column 3 (10)
  Call to set_alt_in_cm in /src/ex.cpp on line 29 column 3 (9)
```

This confirms that the tool works correctly.

## Reproducing Results

The `bugs/` directory contains scripts to direct the tool to refind the 14 bugs described in our paper. For example:

```sh
$ cd bugs/01
$ chmod +x ./recreate.sh
$ ./recreate.sh
```

## Type Deduction

### 1. Build the Type Deduction Docker Image

```sh
# From the root of this directory.
$ cd type_deduction
$ docker image build -t sa4u_type_deduction ./
```

### 2. Validate the Image

```sh
# From the root of this directory.
$ cd type_deduction
$ docker container run  \
    --rm                \
    -it                 \
    -v "$(pwd)":/data   \
    sa4u_type_deduction \
    /data/trace.csv     \
    /data/kernel_variables
```
