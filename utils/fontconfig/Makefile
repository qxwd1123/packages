#
# Copyright (C) 2008-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=fontconfig
PKG_VERSION:=2.13.94
PKG_RELEASE:=3

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://fontconfig.org/release/
PKG_HASH:=a5f052cb73fd479ffb7b697980510903b563bbb55b8f7a2b001fcfb94026003c

PKG_MAINTAINER:=
PKG_LICENSE:=
PKG_LICENSE_FILES:=
PKG_CPE_ID:=cpe:/a:fontconfig_project:fontconfig

PKG_BUILD_DEPENDS:=gperf/host

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/meson.mk

define Package/fontconfig
  SECTION:=xorg-util
  CATEGORY:=Xorg
  SUBMENU:=Font-Utils
  TITLE:=fontconfig
  DEPENDS:=+libpthread +libexpat +libfreetype
  URL:=http://fontconfig.org/
endef

MESON_ARGS += \
	-Ddoc=disabled \
	-Ddoc-txt=disabled \
	-Dnls=disabled \
	-Dtests=disabled \
	-Dtools=enabled

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/fontconfig $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libfontconfig.* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/fontconfig.pc $(1)/usr/lib/pkgconfig/
endef

define Package/fontconfig/install
	$(INSTALL_DIR) $(1)/usr/bin $(1)/usr/lib $(1)/usr/share/fontconfig/conf.avail
	$(INSTALL_DIR) $(1)/etc/fonts/conf.d
	$(CP) $(PKG_INSTALL_DIR)/etc/fonts/fonts.conf $(1)/etc/fonts
	$(CP) $(PKG_INSTALL_DIR)/etc/fonts/conf.d/* $(1)/etc/fonts/conf.d
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/share/fontconfig/conf.avail/* $(1)/usr/share/fontconfig/conf.avail
	$(INSTALL_DIR) $(1)/etc/init.d
#	$(INSTALL_BIN) ./files/fontconfig.init $(1)/etc/init.d/fontconfig
endef

$(eval $(call BuildPackage,fontconfig))
