Notice
======

I'm leaving Github. The main official location for this project is now:
https://codeberg.org/RafaGago/small-project-makefile

# small-project-makefile
GNU makefile for small-medium sized C or C++ projects

The variables used are in the file itself, just some examples.

Simple C binary with sources in the "/src" project subfolder and the makefile on
the project root.

    # Some variables
    ARTIFACT := bin/myprogram

    # Build setup
    LDLIBS += -lpthread -lrt

    include build.mk

Simple C++ library with the makefile in the "build/linux" project subfolder
that just builds the sources under the "src/common" and "src/implementation1"
folders.

    # Some variables
    ARTIFACT      := lib/libmylib
    VERSION_MAJOR := 1
    VERSION_MINOR := 0
    VERSION_REV   := 0

    # Standard directory layout overrides
    THIS_FILE_DIR := $(shell dirname $(realpath $(lastword $(MAKEFILE_LIST))))
    TOP           := $(THIS_FILE_DIR)/../..
    BUILD_DIR     := $(THIS_FILE_DIR)/tmp
    SRC_DIRS      := $(TOP)/src/common $(TOP)/src/implementation1

    # Build setup
    LD ?= $(CXX)

    include build.mk
