cc_library(
  name = 'ubus',
  warning = 'no',
  extra_cppflags = [
    '-Wno-error=sign-compare',
  ],
  defs = [
    'UBUS_UNIX_SOCKET=\\"/var/run/ubus.sock\\"',
    'UBUS_MAX_MSGLEN=1048576',
  ],
  export_incs = [
    '.',
  ],
  srcs = [
    'libubus.c',
    'libubus-io.c',
    'libubus-obj.c',
    'libubus-sub.c',
    'libubus-req.c',
  ],
  deps = [
    '//libubox:ubox',
  ]
)

cc_binary(
  name = 'ubusd',
  warning = 'no',
  extra_cppflags = [
    '-Wno-error=sign-compare',
  ],
  defs = [
    'UBUS_UNIX_SOCKET=\\"/var/run/ubus.sock\\"',
    'UBUS_MAX_MSGLEN=1048576',
  ],
  srcs = [
    'ubusd.c',
    'ubusd_id.c',
    'ubusd_obj.c',
    'ubusd_proto.c',
    'ubusd_event.c',
  ],
  deps = [
    '//libubox:ubox',
  ]
)

cc_binary(
  name = 'ubusc',
  warning = 'no',
  extra_cppflags = [
    '-Wno-error=sign-compare',
  ],
  srcs = [
    'cli.c',
  ],
  deps = [
    ':ubus',
    '//libubox:ubox',
    '//libubox:blobmsg_json',
    '//json-c:json-c',
  ]
)
