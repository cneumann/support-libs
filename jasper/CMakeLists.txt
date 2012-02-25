
CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

IF(JASPER_SRC_DIR)
    PROJECT(jasper C)

    SET(JASPER_TARGET_NAME_SHARED jasper)
    SET(JASPER_TARGET_NAME_STATIC libjasper)

    IF(SEPARATE_INSTALL_DIRS)
        SET(JASPER_RUNTIME_INSTALL_DIR "jasper/bin")
        SET(JASPER_LIBRARY_INSTALL_DIR "jasper/lib")
        SET(JASPER_ARCHIVE_INSTALL_DIR "jasper/lib")
        SET(JASPER_HEADER_INSTALL_DIR  "jasper/include")
    ELSE(SEPARATE_INSTALL_DIRS)
        SET(JASPER_RUNTIME_INSTALL_DIR "bin")
        SET(JASPER_LIBRARY_INSTALL_DIR "lib")
        SET(JASPER_ARCHIVE_INSTALL_DIR "lib")
        SET(JASPER_HEADER_INSTALL_DIR  "include")
    ENDIF(SEPARATE_INSTALL_DIRS)

    SET(C_SRC_FILES)
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/base/jas_cm.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/base/jas_debug.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/base/jas_getopt.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/base/jas_icc.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/base/jas_iccdata.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/base/jas_image.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/base/jas_init.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/base/jas_malloc.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/base/jas_seq.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/base/jas_stream.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/base/jas_string.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/base/jas_tmr.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/base/jas_tvp.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/base/jas_version.c")

    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/bmp/bmp_cod.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/bmp/bmp_dec.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/bmp/bmp_enc.c")

    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/jp2/jp2_cod.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/jp2/jp2_dec.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/jp2/jp2_enc.c")

    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/jpc/jpc_bs.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/jpc/jpc_cs.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/jpc/jpc_dec.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/jpc/jpc_enc.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/jpc/jpc_math.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/jpc/jpc_mct.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/jpc/jpc_mqcod.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/jpc/jpc_mqdec.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/jpc/jpc_mqenc.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/jpc/jpc_qmfb.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/jpc/jpc_t1cod.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/jpc/jpc_t1dec.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/jpc/jpc_t1enc.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/jpc/jpc_t2cod.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/jpc/jpc_t2dec.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/jpc/jpc_t2enc.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/jpc/jpc_tagtree.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/jpc/jpc_tsfb.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/jpc/jpc_util.c")

    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/jpg/jpg_dec.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/jpg/jpg_enc.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/jpg/jpg_val.c")

    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/mif/mif_cod.c")
    
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/pgx/pgx_cod.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/pgx/pgx_dec.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/pgx/pgx_enc.c")

    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/pnm/pnm_cod.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/pnm/pnm_dec.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/pnm/pnm_enc.c")

    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/ras/ras_cod.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/ras/ras_dec.c")
    LIST(APPEND C_SRC_FILES "${JASPER_SRC_DIR}/src/libjasper/ras/ras_enc.c")

    INCLUDE_DIRECTORIES("${JASPER_SRC_DIR}/src/libjasper/include")
    INCLUDE_DIRECTORIES("${LIBJPEG_SRC_DIR}")

    IF(BUILD_SHARED_LIBS)
        ADD_LIBRARY(${JASPER_TARGET_NAME_SHARED} SHARED ${C_SRC_FILES})
        TARGET_LINK_LIBRARIES(${JASPER_TARGET_NAME_SHARED} ${LIBJPEG_TARGET_NAME_SHARED})

        SET_TARGET_PROPERTIES(${TARGET_NAME_SHARED}  PROPERTIES
            DEFINE_SYMBOL "JAS_WIN_MSVC_BUILD"
            DEBUG_POSTFIX "d")

        INSTALL(TARGETS ${TARGET_NAME_SHARED}
            CONFIGURATIONS Release Debug
            RUNTIME DESTINATION ${JASPER_RUNTIME_INSTALL_DIR}
            LIBRARY DESTINATION ${JASPER_LIBRARY_INSTALL_DIR}
            ARCHIVE DESTINATION ${JASPER_ARCHIVE_INSTALL_DIR})
    ENDIF(BUILD_SHARED_LIBS)

    IF(BUILD_STATIC_LIBS)
        ADD_LIBRARY(${JASPER_TARGET_NAME_STATIC} STATIC ${C_SRC_FILES})
        SET_TARGET_PROPERTIES(${TARGET_NAME_STATIC}  PROPERTIES
            DEFINE_SYMBOL "JAS_WIN_MSVC_BUILD"
            DEBUG_POSTFIX "d")

        INSTALL(TARGETS ${TARGET_NAME_STATIC}
            CONFIGURATIONS Release Debug
            RUNTIME DESTINATION ${JASPER_RUNTIME_INSTALL_DIR}
            LIBRARY DESTINATION ${JASPER_LIBRARY_INSTALL_DIR}
            ARCHIVE DESTINATION ${JASPER_ARCHIVE_INSTALL_DIR})
    ENDIF(BUILD_STATIC_LIBS)

    INSTALL(FILES ${C_HDR_FILES}
        DESTINATION ${JASPER_HEADER_INSTALL_DIR}
        PERMISSIONS OWNER_READ OWNER_WRITE
                    GROUP_READ
                    WORLD_READ)

ELSE(JASPER_SRC_DIR)
    MESSAGE(STATUS "JASPER_SRC_DIR not set - can not build jasper")
ENDIF(JASPER_SRC_DIR)
