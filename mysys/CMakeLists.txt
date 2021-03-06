# Copyright (C) 2006 MySQL AB
# 
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; version 2 of the License.
# 
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# 
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA

set ( MYSYS_SOURCES array.c charset-def.c charset.c checksum.c default.c default_modify.c 
  errors.c hash.c list.c md5.c mf_brkhant.c mf_cache.c mf_dirname.c mf_fn_ext.c mf_format.c 
  mf_getdate.c mf_iocache.c mf_iocache2.c mf_keycache.c my_safehash.c mf_keycaches.c 
  mf_loadpath.c mf_pack.c mf_path.c mf_qsort.c mf_qsort2.c mf_radix.c mf_same.c mf_sort.c 
  mf_soundex.c mf_strip.c mf_arr_appstr.c mf_tempdir.c mf_tempfile.c mf_unixpath.c 
  mf_wcomp.c mf_wfile.c mulalloc.c my_access.c my_aes.c my_alarm.c my_alloc.c my_append.c 
  my_bit.c my_bitmap.c my_chmod.c my_chsize.c my_clock.c my_compress.c my_conio.c 
  my_copy.c my_create.c my_delete.c my_div.c my_error.c my_file.c my_fopen.c my_fstream.c 
  my_gethostbyname.c my_gethwaddr.c my_getopt.c my_getsystime.c my_getwd.c my_init.c 
  my_lib.c my_lock.c my_lockmem.c my_malloc.c my_messnc.c my_dup.c my_mkdir.c my_mmap.c 
  my_net.c my_once.c my_open.c my_pread.c my_pthread.c my_quick.c my_read.c my_realloc.c 
  my_redel.c my_rename.c my_seek.c my_sleep.c my_static.c my_symlink.c my_symlink2.c 
  my_sync.c my_thr_init.c my_wincond.c my_winerr.c my_winfile.c my_windac.c my_winthread.c 
  my_write.c ptr_cmp.c queues.c stacktrace.c rijndael.c safemalloc.c sha1.c string.c 
  thr_alarm.c thr_lock.c thr_mutex.c thr_rwlock.c tree.c typelib.c my_vle.c base64.c 
  my_memmem.c my_getpagesize.c lf_alloc-pin.c lf_dynarray.c lf_hash.c my_atomic.c 
  my_getncpus.c my_rnd.c my_uuid.c wqueue.c waiting_threads.c my_port.c )

if ( NOT SOURCE_SUBLIBS )
  set ( CMAKE_C_FLAGS_DEBUG "${CMAKE_C_FLAGS_DEBUG} -DSAFEMALLOC -DSAFE_MUTEX" )

  include_directories ( ${ZLIB_INCLUDE_DIR} ${CMAKE_SOURCE_DIR}/include ${CMAKE_SOURCE_DIR}/mysys )

  add_library ( mysys STATIC ${MYSYS_SOURCES} )
  target_link_libraries ( mysys ${CMAKE_THREAD_LIBS_INIT} )

  if ( MATH_LIBRARY )
    target_link_libraries ( mysys ${MATH_LIBRARY} )
  endif ( MATH_LIBRARY )

endif ( NOT SOURCE_SUBLIBS )
