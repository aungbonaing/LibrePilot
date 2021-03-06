#
# Copyright (c) 2015, The LibrePilot Project, http://www.librepilot.org
# Copyright (c) 2009-2013, The OpenPilot Team, http://www.openpilot.org
# Copyright (c) 2012, PhoenixPilot, http://github.com/PhoenixPilot
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY
# or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License
# for more details.
#
# You should have received a copy of the GNU General Public License along
# with this program; if not, write to the Free Software Foundation, Inc.,
# 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA
#

ifndef FLIGHT_MAKEFILE
    $(error Top level Makefile must be used to build this target)
endif

include ../board-info.mk
include $(FLIGHT_ROOT_DIR)/make/firmware-defs.mk

# ARM DSP library
USE_DSP_LIB ?= NO

# Set to YES to build a FW version that will erase data flash memory
ERASE_FLASH ?= NO

# List of mandatory modules to include
#MODULES += FirmwareIAP
MODULES += gpsp

# Include all camera options
CDEFS += -DPIOS_APPS_MINIMAL

# List C source files here (C dependencies are automatically generated).
# Use file-extension c for "c-only"-files
## The standard CMSIS startup
SRC += $(CMSIS_DEVICEDIR)/system_stm32f0xx.c

## Application Core
SRC += $(OPSYSTEM)/gpsp.c
SRC += $(OPSYSTEM)/pios_board.c
SRC += $(FLIGHTLIB)/ubx_utils.c

SRC += $(PIOSCOMMON)/pios_hmc5x83.c
SRC += $(PIOSCOMMON)/pios_ubx_dcc.c
SRC += $(PIOSCOMMON)/pios_flash_jedec.c

## UAVObjects
SRC += $(FLIGHT_UAVOBJ_DIR)/firmwareiapobj.c
SRC += $(FLIGHT_UAVOBJ_DIR)/systemstats.c

PIOS_OMITS_USB = YES
PIOS_APPS_MINIMAL = YES

include $(FLIGHT_ROOT_DIR)/make/apps-defs.mk
include $(FLIGHT_ROOT_DIR)/make/common-defs.mk
