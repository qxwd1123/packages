# SPDX-License-Identifier: GPL-3.0-only
#
# Copyright (C) 2022 ImmortalWrt.org

include $(TOPDIR)/rules.mk

PKG_NAME:=dos2unix
PKG_VERSION:=7.5.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://waterlan.home.xs4all.nl/dos2unix/ \
                @SF/dos2unix
PKG_HASH:=7a3b01d01e214d62c2b3e04c3a92e0ddc728a385566e4c0356efa66fd6eb95af

PKG_MAINTAINER:=Tianling Shen <cnsztl@immortalwrt.org>
PKG_LICENSE:=BSD-2-Clause
PKG_LICENSE_FILES:=COPYING.txt

PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

MAKE_FLAGS+= D2U_OS=Linux ENABLE_NLS=

define dos2unix/template
  define Package/$(1)
    SECTION:=utils
    CATEGORY:=Utilities
    TITLE:=Text file format converters ($(1))
    URL:=https://waterlan.home.xs4all.nl/dos2unix.html
    PROVIDES:=$(2)
  endef

  define Package/$(1)/description
  Convert text files with DOS or Mac line breaks to Unix line breaks
  and vice versa.

  This package contains the $(1).
  endef

  define Package/$(1)/install
	$$(INSTALL_DIR) $$(1)/usr/bin
	$$(INSTALL_BIN) $$(PKG_INSTALL_DIR)/usr/bin/$(1) $$(1)/usr/bin/
	$$(LN) $(1) $$(1)/usr/bin/$(2)
  endef

  $$(eval $$(call BuildPackage,$(1)))
endef

$(eval $(call dos2unix/template,dos2unix,mac2unix))
$(eval $(call dos2unix/template,unix2dos,unix2mac))
