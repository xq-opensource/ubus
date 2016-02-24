cmake_minimum_required(VERSION 2.6)

PROJECT(ubus C)

SET(UBUS_UNIX_SOCKET "/var/run/ubus.sock")
SET(UBUS_MAX_MSGLEN 1048576)

ADD_DEFINITIONS( -DUBUS_UNIX_SOCKET="${UBUS_UNIX_SOCKET}")
ADD_DEFINITIONS( -DUBUS_MAX_MSGLEN=${UBUS_MAX_MSGLEN})

ADD_LIBRARY(ubus STATIC
  libubus.c
  libubus-io.c
  libubus-obj.c
  libubus-sub.c
  libubus-req.c)

TARGET_LINK_LIBRARIES(ubus ubox)

ADD_EXECUTABLE(ubusd
  ubusd.c
  ubusd_id.c
  ubusd_obj.c
  ubusd_proto.c
  ubusd_event.c)

TARGET_LINK_LIBRARIES(ubusd ubox)

ADD_EXECUTABLE(cli
  cli.c
)

SET_TARGET_PROPERTIES(cli PROPERTIES OUTPUT_NAME ubus)

TARGET_LINK_LIBRARIES(cli
  ubus
  ubox
  blobmsg_json
  json-c
)
