include $(TOPDIR)/rules.mk

PKG_NAME:=apk
PKG_VERSION:=2.14.0
PKG_RELEASE:=1

PKG_SOURCE:=apk-tools-v$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://gitlab.alpinelinux.org/alpine/apk-tools/-/archive/v$(PKG_VERSION)
PKG_HASH:=4c6db13039280814a10a3b3d89b29837b59769c69214a1861997e088eac107a5
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)

PKG_MAINTAINER:=Paul Spooren <mail@aparcar.org>
PKG_LICENSE:=GPL-2.0-only
PKG_LICENSE_FILES:=LICENSE

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/apk
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=apk package manager
  DEPENDS:=+zlib +libopenssl @!arc
  URL:=$(PKG_SOURCE_URL)
endef

define Package/alpine-keys
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Alpine apk public signing keys
  DEPENDS:=apk
endef

define Package/alpine-repositories
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Official Alpine repositories
  DEPENDS:=apk
endef

MAKE_FLAGS += LUA=no

define Package/apk/install
	$(INSTALL_DIR) $(1)/lib/apk/db

	$(INSTALL_DIR) $(1)/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/sbin/apk $(1)/bin/apk

	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/lib/* $(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/apk.pc \
		$(1)/usr/lib/pkgconfig/

	$(INSTALL_DIR) $(1)/etc/apk/
	echo $(ARCH) > $(1)/etc/apk/arch
	touch $(1)/etc/apk/world
endef

define Package/alpine-keys/install
	$(INSTALL_DIR) $(1)/etc/apk/keys
	$(INSTALL_DATA) ./files/alpine-keys/* $(1)/etc/apk/keys
endef

define Package/alpine-repositories/install
	$(INSTALL_DIR) $(1)/etc/apk/keys
	$(INSTALL_DATA) ./files/alpine-repositories $(1)/etc/apk/repositories
endef

$(eval $(call BuildPackage,apk))
$(eval $(call BuildPackage,alpine-keys))
$(eval $(call BuildPackage,alpine-repositories))
