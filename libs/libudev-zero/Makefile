# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libudev-zero
PKG_VERSION:=1.0.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/illiliti/libudev-zero/tar.gz/$(PKG_VERSION)?
PKG_HASH:=c4cf149ea96295c1e6e86038d10c725344c751982ed4a790b06c76776923e0ea

PKG_MAINTAINER:=Daniel Golle <daniel@makrotopia.org>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/libudev-zero
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Drop-in replacement for libudev
  URL:=https://github.com/illiliti/libudev-zero
  DEPENDS:=+libevdev
  PROVIDES:=libudev
  CONFLICTS:=libudev eudev udev
endef

MAKE_FLAGS += \
	PREFIX=/usr

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/libudev.h $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libudev.{a,so*} $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/libudev.pc $(1)/usr/lib/pkgconfig/
endef

define Package/libudev-zero/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libudev.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libudev-zero))
