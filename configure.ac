AC_PREREQ(2.53)
AC_INIT(mokomaze, 0.5, http://mokomaze.projects.openmoko.org/)
AM_INIT_AUTOMAKE()
AC_CONFIG_SRCDIR(src/main.c)
AM_CONFIG_HEADER(config.h)
AM_MAINTAINER_MODE

AC_ISC_POSIX
AC_PROG_CC
AC_PROG_CC_STDC
AC_STDC_HEADERS
AC_PROG_LIBTOOL
AC_PROG_INTLTOOL([0.35.0])

dnl i18n support
GETTEXT_PACKAGE=AC_PACKAGE_NAME
AC_DEFINE_UNQUOTED(GETTEXT_PACKAGE, "$GETTEXT_PACKAGE", [Gettext package])
AC_SUBST(GETTEXT_PACKAGE)
AM_GLIB_GNU_GETTEXT

PKG_CHECK_MODULES(SDL, sdl >= 1.0.0)
AC_CHECK_LIB(SDL_image, IMG_Load, , [AC_MSG_ERROR([*** SDL_image not found!])])
AC_CHECK_LIB(SDL_ttf, TTF_OpenFont, , [AC_MSG_ERROR([*** SDL_ttf not found!])])
AC_CHECK_LIB(ode, dInitODE, , [AC_MSG_ERROR([*** ODE not found!])])

AC_SUBST(SDL)

#--------------------------------------------------------------
if test "x"${FONTDIR} == "x"; then
AC_SUBST(MAZEFONTDIR, /usr/share/fonts/truetype/ttf-liberation)
else
AC_SUBST(MAZEFONTDIR, ${FONTDIR})
fi

AC_ARG_ENABLE(rgb-swap,
    [  --enable-rgb-swap       swap color components (R<->B) ],
    [use_rgb_swap="yes"], [use_rgb_swap="no"])
AM_CONDITIONAL(RGBSWAP, test x$use_rgb_swap != xno)
#--------------------------------------------------------------

AC_OUTPUT([
Makefile
src/Makefile
data/Makefile
po/Makefile.in
])

