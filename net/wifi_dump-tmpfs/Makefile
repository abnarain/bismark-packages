# Copyright (C) 2006-2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=wifi_dump-tmpfs
PKG_RELEASE:=1
PKG_VERSION:=HEAD

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=git://github.com/abnarain/wifi_dump-tmpfs.git
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_PROTO:=git
#GIT_URL:=git:/
#GIT_URL:=src/

include $(INCLUDE_DIR)/package.mk

define Package/wifi_dump-tmpfs
	SECTION:=net
	CATEGORY:=Network
	TITLE:=BISmark Wireless Measurements tool 
	URL:=http://doesnotexist.com
	DEPENDS:=+zlib +bismark-data-transmit 
endef

define Package/bismark-active-tmpfs/description
 This tool collects wireless traces in monitor mode. This tool is a part of infrastructure to understand wireless home networks.
endef

define Package/wifi_dump-tmpfs/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_DIR) $(1)/tmp/wifi_dump
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/wifi_dump $(1)/usr/bin/wifi_dump.bin
	$(INSTALL_BIN) ./files/etc/init.d/wifi_dump $(1)/etc/init.d/wifi_dump
	$(INSTALL_BIN) ./files/usr/bin/wifi_dump $(1)/usr/bin/wifi_dump
endef

 
define Package/wifi_dump-tmpfs/postinst
#!/bin/sh
/tmp/etc/init.d/wifi_dump enable
/tmp/etc/init.d/wifi_dump restart
endef

define Package/wifi_dump-tmpfs/prerm
#!/bin/sh
/tmp/etc/init.d/wifi_dump stop
endef

$(eval $(call BuildPackage,wifi_dump-tmpfs))
