#
# CMake definition for PDCurses
#

cmake_minimum_required (VERSION 3.13)
project (pdcurses)

include_directories(.)
include_directories(pdcurses)
include_directories(win32)

set(COMMON_SOURCES
	pdcurses/addch.c
	pdcurses/addchstr.c
	pdcurses/addstr.c
	pdcurses/attr.c
	pdcurses/beep.c
	pdcurses/bkgd.c
	pdcurses/border.c
	pdcurses/clear.c
	pdcurses/color.c
	pdcurses/debug.c
	pdcurses/delch.c
	pdcurses/deleteln.c
	pdcurses/getch.c
	pdcurses/getstr.c
	pdcurses/getyx.c
	pdcurses/inch.c
	pdcurses/inchstr.c
	pdcurses/initscr.c
	pdcurses/inopts.c
	pdcurses/insch.c
	pdcurses/insstr.c
	pdcurses/instr.c
	pdcurses/kernel.c
	pdcurses/keyname.c
	pdcurses/mouse.c
	pdcurses/move.c
	pdcurses/outopts.c
	pdcurses/overlay.c
	pdcurses/pad.c
	pdcurses/panel.c
	pdcurses/printw.c
	pdcurses/refresh.c
	pdcurses/scanw.c
	pdcurses/scroll.c
	pdcurses/scr_dump.c
	pdcurses/slk.c
	pdcurses/termattr.c
	pdcurses/touch.c
	pdcurses/util.c
	pdcurses/window.c
  )

if(WIN32)
  set(PLATFORM_SOURCES 
	wincon/pdcclip.c
	wincon/pdcdisp.c
	wincon/pdcgetsc.c
	wincon/pdckbd.c
	wincon/pdcscrn.c
	wincon/pdcsetsc.c
	wincon/pdcutil.c
    )
endif()

if(MSVC)
  add_definitions(-D_CRT_SECURE_NO_WARNINGS -D_CRT_NONSTDC_NO_DEPRECATE -D_WINSOCK_DEPRECATED_NO_WARNINGS)
endif()

add_library(pdcurses ${COMMON_SOURCES} ${PLATFORM_SOURCES})

set(PDCURSES_INCLUDE_DIRS ${PROJECT_SOURCE_DIR} 
                          ${PROJECT_SOURCE_DIR}/pdcurses
                          ${PROJECT_SOURCE_DIR}/win32
                          PARENT_SCOPE)
set(CURSES_LIBRARIES pdcurses PARENT_SCOPE)
