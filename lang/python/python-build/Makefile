#
# Copyright (C) 2023 Jeffery To
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-build
PKG_VERSION:=0.10.0
PKG_RELEASE:=2

PYPI_NAME:=build
PKG_HASH:=d5b71264afdb5951d6704482aac78de887c80691c52b88a9ad195983ca2c9269

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Jeffery To <jeffery.to@gmail.com>

PKG_HOST_ONLY:=1
HOST_BUILD_DEPENDS:= \
	python3/host \
	python-installer/host \
	python-flit-core/host \
	python-packaging/host \
	python-pyproject-hooks/host

PYTHON3_HOST_BUILD_VARS:=PYTHONPATH=src

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/host-build.mk
include ../python3-package.mk
include ../python3-host-build.mk

define Package/python3-build
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=A simple, correct Python build frontend
  URL:=https://github.com/pypa/build
  DEPENDS:=+python3-light +python3-logging
  BUILDONLY:=1
endef

define Package/python3-build/description
A simple, correct PEP 517 build frontend.

build will invoke the PEP 517 hooks to build a distribution package. It
is a simple build tool and does not perform any dependency management.
endef

$(eval $(call Py3Package,python3-build))
$(eval $(call BuildPackage,python3-build))
$(eval $(call BuildPackage,python3-build-src))
$(eval $(call HostBuild))
