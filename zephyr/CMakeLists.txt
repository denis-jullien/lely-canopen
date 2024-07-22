if(CONFIG_LELY_CANOPEN)

  set(LELY_SRC_DIR ${ZEPHYR_CURRENT_MODULE_DIR}/src)

  zephyr_compile_definitions(
  #        LELY_NO_MALLOC
          LELY_NO_THREADS
  #        LELY_NO_ERRNO
          LELY_NO_STDIO
          LELY_HAVE_TIMESPEC=1
          LELY_HAVE_ITIMERSPEC=1
          LELY_NO_CO_DCF
          LELY_NO_DIAG
  )

  zephyr_include_directories(
    ${ZEPHYR_CURRENT_MODULE_DIR}/include
    ${LELY_SRC_DIR}/co
    .
  )


  zephyr_library()


  zephyr_library_sources(
          ${LELY_SRC_DIR}/co/crc.c
          ${LELY_SRC_DIR}/co/csdo.c
          ${LELY_SRC_DIR}/co/dcf.c
          ${LELY_SRC_DIR}/co/dev.c
          ${LELY_SRC_DIR}/co/emcy.c
          ${LELY_SRC_DIR}/co/gw.c
          ${LELY_SRC_DIR}/co/gw_txt.c
          ${LELY_SRC_DIR}/co/lss.c
          ${LELY_SRC_DIR}/co/nmt.c
          ${LELY_SRC_DIR}/co/nmt_boot.c
          ${LELY_SRC_DIR}/co/nmt_cfg.c
          ${LELY_SRC_DIR}/co/nmt_hb.c
          ${LELY_SRC_DIR}/co/nmt_hb.h
          ${LELY_SRC_DIR}/co/nmt_srv.c
          ${LELY_SRC_DIR}/co/nmt_srv.h
          ${LELY_SRC_DIR}/co/obj.c
          ${LELY_SRC_DIR}/co/pdo.c
          ${LELY_SRC_DIR}/co/rpdo.c
          ${LELY_SRC_DIR}/co/sdev.c
          ${LELY_SRC_DIR}/co/sdo.c
          ${LELY_SRC_DIR}/co/sdo.h
          ${LELY_SRC_DIR}/co/ssdo.c
          ${LELY_SRC_DIR}/co/sync.c
          ${LELY_SRC_DIR}/co/time.c
          ${LELY_SRC_DIR}/co/tpdo.c
          ${LELY_SRC_DIR}/co/type.c
          ${LELY_SRC_DIR}/co/val.c
          ${LELY_SRC_DIR}/co/wtm.c

          ${LELY_SRC_DIR}/util/errnum.c
          ${LELY_SRC_DIR}/util/rbtree.c
          ${LELY_SRC_DIR}/util/endian.c
          ${LELY_SRC_DIR}/util/membuf.c
          ${LELY_SRC_DIR}/util/pheap.c
#          ${LELY_SRC_DIR}/util/lex.c
#          ${LELY_SRC_DIR}/util/print.c
#          ${LELY_SRC_DIR}/util/fwbuf.c
#          ${LELY_SRC_DIR}/util/frbuf.c
          ${LELY_SRC_DIR}/util/diag.c

          ${LELY_SRC_DIR}/can/net.c
          ${LELY_SRC_DIR}/can/msg.c
          ${LELY_SRC_DIR}/can/buf.c
  )

#   zephyr_library_sources_ifdef(CONFIG_CANOPENNODE_SYNC_THREAD canopen_sync.c)
#   zephyr_library_sources_ifdef(CONFIG_CANOPENNODE_STORAGE canopen_storage.c)
#   zephyr_library_sources_ifdef(CONFIG_CANOPENNODE_LEDS canopen_leds.c)
#   zephyr_library_sources_ifdef(CONFIG_CANOPENNODE_PROGRAM_DOWNLOAD canopen_program.c)

endif()