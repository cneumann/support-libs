
CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

IF(LIBTIFF_SRC_DIR)

    PROJECT(tiff C)

    SET(TARGET_NAME_SHARED ${LIBTIFF_TARGET_NAME_SHARED})
    SET(TARGET_NAME_STATIC ${LIBTIFF_TARGET_NAME_STATIC})

    EXECUTE_PROCESS(
        COMMAND "${CMAKE_COMMAND}" "-E" "copy_if_different"
        "${LIBTIFF_SRC_DIR}/libtiff/tif_config.vc.h"
        "${LIBTIFF_SRC_DIR}/libtiff/tif_config.h")

    EXECUTE_PROCESS(
        COMMAND "${CMAKE_COMMAND}" "-E" "copy_if_different"
        "${LIBTIFF_SRC_DIR}/libtiff/tiffconf.vc.h"
        "${LIBTIFF_SRC_DIR}/libtiff/tiffconf.h")

    SET(C_SRC_FILES)
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_aux.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_close.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_codec.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_color.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_compress.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_dir.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_dirinfo.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_dirread.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_dirwrite.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_dumpmode.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_error.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_extension.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_fax3.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_fax3sm.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_flush.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_getimage.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_jbig.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_jpeg.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_luv.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_lzw.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_next.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_ojpeg.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_open.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_packbits.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_pixarlog.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_predict.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_print.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_read.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_strip.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_swab.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_thunder.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_tile.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_unix.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_version.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_warning.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_write.c")
    LIST(APPEND C_SRC_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_zip.c")

    SET(C_HDR_FILES)
    LIST(APPEND C_HDR_FILES "${LIBTIFF_SRC_DIR}/libtiff/tif_config.h")
    LIST(APPEND C_HDR_FILES "${LIBTIFF_SRC_DIR}/libtiff/tiffconf.h")
    LIST(APPEND C_HDR_FILES "${LIBTIFF_SRC_DIR}/libtiff/tiff.h")
    LIST(APPEND C_HDR_FILES "${LIBTIFF_SRC_DIR}/libtiff/tiffvers.h")

    SET(TEST0_C_SRC_FILES)
    LIST(APPEND TEST0_C_SRC_FILES "${LIBTIFF_SRC_DIR}/test/ascii_tag.c")

    SET(TEST0_TARGET_NAME_SHARED "libtiff-ascii_tag-shared")
    SET(TEST0_TARGET_NAME_STATIC "libtiff-ascii_tag-static")

    SET(TEST1_C_SRC_FILES)
    LIST(APPEND TEST1_C_SRC_FILES "${LIBTIFF_SRC_DIR}/test/strip_rw.c")
    LIST(APPEND TEST1_C_SRC_FILES "${LIBTIFF_SRC_DIR}/test/strip.c")
    LIST(APPEND TEST1_C_SRC_FILES "${LIBTIFF_SRC_DIR}/test/test_arrays.c")

    SET(TEST1_TARGET_NAME_SHARED "libtiff-strip_rw-shared")
    SET(TEST1_TARGET_NAME_STATIC "libtiff-strip_rw-static")

    INCLUDE_DIRECTORIES("${LIBTIFF_SRC_DIR}/libtiff")

    IF(BUILD_SHARED_LIBS)
        ADD_LIBRARY(${TARGET_NAME_SHARED} SHARED
            ${C_SRC_FILES}
            "${LIBTIFF_SRC_DIR}/libtiff/libtiff.def")

        SET_TARGET_PROPERTIES(${TARGET_NAME_SHARED}  PROPERTIES
            DEFINE_SYMBOL "ZLIB_DLL"
            DEBUG_POSTFIX "d")

        TARGET_LINK_LIBRARIES(${TARGET_NAME_SHARED} ${ZLIB_TARGET_NAME_SHARED})

        INSTALL(TARGETS ${TARGET_NAME_SHARED}
            CONFIGURATIONS Release Debug
            RUNTIME DESTINATION bin
            LIBRARY DESTINATION lib
            ARCHIVE DESTINATION lib)

        IF(BUILD_TESTS)
            ADD_EXECUTABLE(${TEST0_TARGET_NAME_SHARED} ${TEST0_C_SRC_FILES})
            TARGET_LINK_LIBRARIES(${TEST0_TARGET_NAME_SHARED} ${TARGET_NAME_SHARED})

            ADD_EXECUTABLE(${TEST1_TARGET_NAME_SHARED} ${TEST1_C_SRC_FILES})
            TARGET_LINK_LIBRARIES(${TEST1_TARGET_NAME_SHARED} ${TARGET_NAME_SHARED})
        ENDIF(BUILD_TESTS)
    ENDIF(BUILD_SHARED_LIBS)

    IF(BUILD_STATIC_LIBS)
        ADD_LIBRARY(${TARGET_NAME_STATIC} STATIC ${C_SRC_FILES})

        SET_TARGET_PROPERTIES(${TARGET_NAME_STATIC}  PROPERTIES
            DEBUG_POSTFIX "d")

        INSTALL(TARGETS ${TARGET_NAME_STATIC}
            CONFIGURATIONS Release Debug
            RUNTIME DESTINATION bin
            LIBRARY DESTINATION lib
            ARCHIVE DESTINATION lib)

        IF(BUILD_TESTS)
            ADD_EXECUTABLE(${TEST0_TARGET_NAME_STATIC} ${TEST0_C_SRC_FILES})
            TARGET_LINK_LIBRARIES(${TEST0_TARGET_NAME_STATIC} ${TARGET_NAME_STATIC})

            ADD_EXECUTABLE(${TEST1_TARGET_NAME_STATIC} ${TEST1_C_SRC_FILES})
            TARGET_LINK_LIBRARIES(${TEST1_TARGET_NAME_STATIC} ${TARGET_NAME_STATIC})
        ENDIF(BUILD_TESTS)
    ENDIF(BUILD_STATIC_LIBS)

    INSTALL(FILES ${C_HDR_FILES}
        DESTINATION include
        PERMISSIONS OWNER_READ OWNER_WRITE
                    GROUP_READ
                    WORLD_READ)

ELSE(LIBTIFF_SRC_DIR)
    MESSAGE(STATUS "LIBTIFF_SRC_DIR not set - can not build libtiff")
ENDIF(LIBTIFF_SRC_DIR)
