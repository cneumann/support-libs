
CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

PROJECT(supportlibs)

OPTION(BUILD_SHARED_LIBS "Build shared libraries" ON)
OPTION(BUILD_STATIC_LIBS "Build static libraries" OFF)
OPTION(BUILD_TESTS       "Build test/example programs" OFF)
OPTION(SEPARATE_INSTALL_DIRS "Install libraries/headers to separate dirs" OFF)

FUNCTION(LOCATE_SRC_DIR VARNAME BASEDIR HEADERFILE HEADERDIR)
    FILE(GLOB_RECURSE CANDLIST RELATIVE "${BASEDIR}" FOLLOW_SYMLINKS "${BASEDIR}/${HEADERFILE}")
    
    FOREACH(cand ${CANDLIST})
        STRING(REPLACE "${HEADERDIR}" "" canddir "${cand}")
        SET(dir "${BASEDIR}/${canddir}")

        IF(EXISTS "${dir}/${HEADERDIR}")
            SET(${VARNAME} "${dir}" PARENT_SCOPE)
            MESSAGE(STATUS "Found ${VARNAME} = '${dir}'")
            BREAK()
        ENDIF(EXISTS "${dir}/${HEADERDIR}")
    ENDFOREACH(cand)
ENDFUNCTION(LOCATE_SRC_DIR)

# try to deduce <LIB>_SRC_DIR from ROOT_SRC_DIR
IF(NOT ZLIB_SRC_DIR AND ROOT_SRC_DIR AND EXISTS "${ROOT_SRC_DIR}/zlib")
    LOCATE_SRC_DIR(ZLIB_SRC_DIR "${ROOT_SRC_DIR}/zlib" "zlib.h" "zlib.h")
ENDIF(NOT ZLIB_SRC_DIR AND ROOT_SRC_DIR AND EXISTS "${ROOT_SRC_DIR}/zlib")

IF(NOT ILMBASE_SRC_DIR AND ROOT_SRC_DIR AND EXISTS "${ROOT_SRC_DIR}/openexr")
    LOCATE_SRC_DIR(ILMBASE_SRC_DIR "${ROOT_SRC_DIR}/openexr" "half.h" "Half/half.h")
ENDIF(NOT ILMBASE_SRC_DIR AND ROOT_SRC_DIR AND EXISTS "${ROOT_SRC_DIR}/openexr")

IF(NOT OPENEXR_SRC_DIR AND ROOT_SRC_DIR AND EXISTS "${ROOT_SRC_DIR}/openexr")
    LOCATE_SRC_DIR(OPENEXR_SRC_DIR "${ROOT_SRC_DIR}/openexr" "ImfIO.h" "IlmImf/ImfIO.h")
ENDIF(NOT OPENEXR_SRC_DIR AND ROOT_SRC_DIR AND EXISTS "${ROOT_SRC_DIR}/openexr")

IF(NOT LIBJPEG_SRC_DIR AND ROOT_SRC_DIR AND EXISTS "${ROOT_SRC_DIR}/libjpeg")
    LOCATE_SRC_DIR(LIBJPEG_SRC_DIR "${ROOT_SRC_DIR}/libjpeg" "jpeglib.h" "jpeglib.h")
ENDIF(NOT LIBJPEG_SRC_DIR AND ROOT_SRC_DIR AND EXISTS "${ROOT_SRC_DIR}/libjpeg")

IF(NOT LIBPNG_SRC_DIR AND ROOT_SRC_DIR AND EXISTS "${ROOT_SRC_DIR}/libpng")
    LOCATE_SRC_DIR(LIBPNG_SRC_DIR "${ROOT_SRC_DIR}/libpng" "png.h" "png.h")
ENDIF(NOT LIBPNG_SRC_DIR AND ROOT_SRC_DIR AND EXISTS "${ROOT_SRC_DIR}/libpng")

IF(NOT LIBTIFF_SRC_DIR AND ROOT_SRC_DIR AND EXISTS "${ROOT_SRC_DIR}/libtiff")
    LOCATE_SRC_DIR(LIBTIFF_SRC_DIR "${ROOT_SRC_DIR}/libtiff" "tiff.h" "libtiff/tiff.h")
ENDIF(NOT LIBTIFF_SRC_DIR AND ROOT_SRC_DIR AND EXISTS "${ROOT_SRC_DIR}/libtiff")

IF(NOT JASPER_SRC_DIR AND ROOT_SRC_DIR AND EXISTS "${ROOT_SRC_DIR}/jasper")
    LOCATE_SRC_DIR(JASPER_SRC_DIR "${ROOT_SRC_DIR}/jasper" "jasper.h" "src/libjasper/include/jasper/jasper.h")
ENDIF(NOT JASPER_SRC_DIR AND ROOT_SRC_DIR AND EXISTS "${ROOT_SRC_DIR}/jasper")

IF(NOT OPENJPEG_SRC_DIR AND ROOT_SRC_DIR AND EXISTS "${ROOT_SRC_DIR}/openjpeg")
    LOCATE_SRC_DIR(OPENJPEG_SRC_DIR "${ROOT_SRC_DIR}/openjpeg" "openjpeg.h" "libopenjpeg/openjpeg.h")
ENDIF(NOT OPENJPEG_SRC_DIR AND ROOT_SRC_DIR AND EXISTS "${ROOT_SRC_DIR}/openjpeg")


SET(LIBJPEG_TARGET_NAME_SHARED jpeg)
SET(LIBJPEG_TARGET_NAME_STATIC libjpeg)

SET(LIBPNG_TARGET_NAME_SHARED png)
SET(LIBPNG_TARGET_NAME_STATIC libpng)

SET(LIBTIFF_TARGET_NAME_SHARED tiff)
SET(LIBTIFF_TARGET_NAME_STATIC libtiff)

SET(ZLIB_TARGET_NAME_SHARED zlib)
SET(ZLIB_TARGET_NAME_STATIC libzlib)

ADD_SUBDIRECTORY(zlib)
ADD_SUBDIRECTORY(OpenEXR)
ADD_SUBDIRECTORY(libjpeg)
ADD_SUBDIRECTORY(libpng)
ADD_SUBDIRECTORY(libtiff)
ADD_SUBDIRECTORY(jasper)
ADD_SUBDIRECTORY(openjpeg)
