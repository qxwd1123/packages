#
# Copyright (C) 2017 Philip Prindeville, Redfish Solutions, LLC
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=perl-text-csv_xs
PKG_VERSION:=1.52
PKG_RELEASE:=1

PKG_SOURCE:=Text-CSV_XS-$(PKG_VERSION).tgz
PKG_SOURCE_URL:=https://cpan.metacpan.org/authors/id/H/HM/HMBRAND
PKG_HASH:=e415aa705badf84b359dc4c0f0c982f1bf708481daa14756f3136e7c89c0e41d
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)

PKG_MAINTAINER:=Philip Prindeville <philipp@redfish-solutions.com>
PKG_LICENSE:=GPL-1.0-or-later Artistic-1.0-Perl

include $(INCLUDE_DIR)/package.mk
include ../perl/perlmod.mk

define Package/perl-text-csv_xs
  SUBMENU:=Perl
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Text comma-separated values manipulation routines
  URL:=https://search.cpan.org/dist/Text-CSV_XS/
  DEPENDS:=perl +perlbase-essential +perlbase-config +perlbase-io +perlbase-dynaloader
endef

define Build/Configure
        $(call perlmod/Configure,,)
endef

define Build/Compile
        $(call perlmod/Compile,,)
endef

define Package/perl-text-csv_xs/install
        $(call perlmod/Install,$(1),Text Text/CSV_XS.pm auto/Text/CSV_XS)
endef


$(eval $(call BuildPackage,perl-text-csv_xs))
