#
# Copyright (C) 2006 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=populatefs
PKG_VERSION:=0.9

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=git://github.com/morriswinkler/populatefs
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=73c345c134cbb4cde5e8557c9f83c93b63c92ee5
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_CAT:=zcat

include $(INCLUDE_DIR)/host-build.mk

define Host/Configure
	true
endef

define Host/Compile
	CC=$(HOSTCC) \
	CFLAGS=" -fPIC -Wall $(HOST_CFLAGS)" \
	LDFLAGS=$(HOST_LDFLAGS) \
	EXTRAVERSION="-openwrt" \
	$(MAKE) -C $(HOST_BUILD_DIR) \
		all
endef

define Host/Install
	install -m0755 $(HOST_BUILD_DIR)/src/populatefs $(STAGING_DIR_HOST)/bin/
endef

define Host/Clean
	rm -f $(STAGING_DIR_HOST)/bin/genext2fs
endef

$(eval $(call HostBuild))
