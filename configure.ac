#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.68])
AC_INIT([mahimahi], [0.1], [ravinet@mit.edu])
AM_INIT_AUTOMAKE([foreign])
AC_CONFIG_SRCDIR([delayshell.cc])
AC_CONFIG_HEADERS([config.h])

# Add picky CXXFLAGS
CPPFLAGS="-std=c++11 -pthread"
# PICKY_CXXFLAGS="-pedantic -Wall -Wextra -Weffc++ -Werror -fno-default-inline"
PICKY_CXXFLAGS="-pedantic -Wall -Wextra -Weffc++ -fno-default-inline"
AC_SUBST([PICKY_CXXFLAGS])

# Checks for programs.
AC_PROG_CXX
AC_PROG_RANLIB

AC_ARG_VAR([IPTABLES], [path to iptables])
AC_PATH_PROG([IPTABLES], [iptables], [no], [$PATH$PATH_SEPARATOR/sbin$PATH_SEPARATOR/usr/sbin$PATH_SEPARATOR/bin$PATH_SEPARATOR/usr/bin])
if test "$IPTABLES" = "no"; then
  AC_MSG_ERROR([iptables is required])
fi
AC_DEFINE_UNQUOTED([IPTABLES], ["$IPTABLES"], [path to iptables])

AC_ARG_VAR([IP], [path to ip])
AC_PATH_PROG([IP], [ip], [no], [$PATH$PATH_SEPARATOR/sbin$PATH_SEPARATOR/usr/sbin$PATH_SEPARATOR/bin$PATH_SEPARATOR/usr/bin])
if test "$IP" = "no"; then
  AC_MSG_ERROR([ip is required])
fi
AC_DEFINE_UNQUOTED([IP], ["$IP"], [path to ip])

AC_ARG_VAR([APACHE2], [path to apache2])
AC_PATH_PROG([APACHE2], [apache2], [no], [$PATH$PATH_SEPARATOR/sbin$PATH_SEPARATOR/usr/sbin$PATH_SEPARATOR/bin$PATH_SEPARATOR/usr/bin])
if test "$APACHE2" = "no"; then
  AC_MSG_ERROR([apache2 is required])
fi
AC_DEFINE_UNQUOTED([APACHE2], ["$APACHE2"], [path to apache2])

AC_ARG_VAR([DNSMASQ], [path to dnsmasq])
AC_PATH_PROG([DNSMASQ], [dnsmasq], [no], [$PATH$PATH_SEPARATOR/sbin$PATH_SEPARATOR/usr/sbin$PATH_SEPARATOR/bin$PATH_SEPARATOR/usr/bin])
if test "$DNSMASQ" = "no"; then
  AC_MSG_ERROR([dnsmasq is required])
fi
AC_DEFINE_UNQUOTED([DNSMASQ], ["$DNSMASQ"], [path to dnsmasq])

AC_PATH_PROG([PROTOC], [protoc], [])
AS_IF([test x"$PROTOC" = x],
  [AC_MSG_ERROR([cannot find protoc, the Protocol Buffers compiler])])

# Checks for apache configuration modules
AC_CHECK_FILE([/usr/lib/apache2/modules/mod_dir.so], [],
              [AC_MSG_ERROR([apache2 mod_dir.so is required])])

AC_DEFINE_UNQUOTED([MOD_DIR], ["/usr/lib/apache2/modules/mod_dir.so"], [path to apache2 mod_dir])

AC_CHECK_FILE([/usr/lib/apache2/modules/mod_mpm_prefork.so], [],
              [AC_MSG_ERROR([apache2 mod_mpm_prefork.so is required])])

AC_DEFINE_UNQUOTED([MOD_MPM_PREFORK], ["/usr/lib/apache2/modules/mod_mpm_prefork.so"], [path to apache2 mod_mpm_prefork])

AC_CHECK_FILE([/usr/lib/apache2/modules/mod_mime.so], [],
              [AC_MSG_ERROR([apache2 mod_mime.so is required])])

AC_DEFINE_UNQUOTED([MOD_MIME], ["/usr/lib/apache2/modules/mod_mime.so"], [path to apache2 mod_mime])

AC_CHECK_FILE([/usr/lib/apache2/modules/mod_authz_core.so], [],
              [AC_MSG_ERROR([apache2 mod_authz_core.so is required])])

AC_DEFINE_UNQUOTED([MOD_AUTHZ_CORE], ["/usr/lib/apache2/modules/mod_authz_core.so"], [path to apache2 mod_authz_core])

AC_CHECK_FILE([/usr/lib/apache2/modules/mod_cgi.so], [],
              [AC_MSG_ERROR([apache2 mod_cgi.so is required])])

AC_DEFINE_UNQUOTED([MOD_CGI], ["/usr/lib/apache2/modules/mod_cgi.so"], [path to apache2 mod_cgi])

AC_CHECK_FILE([/usr/lib/apache2/modules/mod_rewrite.so], [],
              [AC_MSG_ERROR([apache2 mod_rewrite.so is required])])

AC_DEFINE_UNQUOTED([MOD_REWRITE], ["/usr/lib/apache2/modules/mod_rewrite.so"], [path to apache2 mod_rewrite])

AC_CHECK_FILE([/usr/lib/apache2/modules/mod_env.so], [],
	      [AC_MSG_ERROR([apache2 mod_env.so is required])])

AC_DEFINE_UNQUOTED([MOD_ENV], ["/usr/lib/apache2/modules/mod_env.so"], [path to apache2 mod_env])

AC_CHECK_FILE([/usr/lib/apache2/modules/mod_ssl.so], [],
              [AC_MSG_ERROR([apache2 mod_ssl.so is required])])

AC_DEFINE_UNQUOTED([MOD_SSL], ["/usr/lib/apache2/modules/mod_ssl.so"], [path to apache2 mod_ssl])

# Checks for SSL certificate file
AC_CHECK_FILE([/etc/ssl/certs/ssl-cert-snakeoil.pem], [],
              [AC_MSG_ERROR([ssl certificate file is required])])

AC_DEFINE_UNQUOTED([MOD_SSL_CERTIFICATE_FILE], ["/etc/ssl/certs/ssl-cert-snakeoil.pem"], [path to ssl certificate file])

AC_DEFINE_UNQUOTED([MOD_SSL_KEY], ["/etc/ssl/private/ssl-cert-snakeoil.key"], [path to ssl key])

# Checks for replayshell cgi script
AC_DEFINE_UNQUOTED([REPLAYSERVER], ["/usr/local/bin/nph-replayserver.cgi"], [path to nph-replayserver.cgi])

# Checks for libraries.
PKG_CHECK_MODULES([protobuf], [protobuf])

# Checks for header files.

# Checks for typedefs, structures, and compiler characteristics.

# Checks for library functions.

AC_CONFIG_FILES([Makefile protobufs/Makefile])
AC_OUTPUT
