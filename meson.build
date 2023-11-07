project('libutp', ['cpp', 'c'],
  default_options: [
    'cpp_std=c++11',
    'c_std=c11',
    'warning_level=3',
    'default_library=static',
    'buildtype=release',
    'cpp_rtti=false',
    'cpp_eh=none',
  ])

utp_lib = library('utp', [
  './utp_api.cpp',
  './utp_callbacks.cpp',
  './utp_hash.cpp',
  './utp_internal.cpp',
  './utp_packedsockaddr.cpp',
  './utp_utils.cpp',
], cpp_args: [
  '-DPOSIX',
  '-Wno-unused-parameter',
  '-Wno-unused-variable',
  '-Wno-unused-const-variable',
  '-Wno-sign-compare',
  '-fpermissive',
  '-Wno-zero-length-array',
  '-Wno-format-pedantic',
])

utp_dep = declare_dependency(
  link_with: utp_lib,
  include_directories: '.',
)

if get_option('ucat').enabled()
  ucat_exe = executable('ucat', [
    './ucat.c'
  ], dependencies: utp_dep, c_args: [
    '-Wno-gnu-pointer-arith',
    '-Wno-unused-parameter',
  ])
endif
