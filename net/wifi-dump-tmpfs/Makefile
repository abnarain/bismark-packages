# Copyright (C) 2006-2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=wifi-dump-tmpfs
PKG_RELEASE:=6
PKG_VERSION:=HEAD

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=git://github.com/abnarain/wifi_dump-tmpfs.git
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_PROTO:=git
#GIT_URL:=git:/
#GIT_URL:=src/

include $(INCLUDE_DIR)/package.mk

define Package/wifi-dump-tmpfs
	SECTION:=net
	CATEGORY:=Network
	TITLE:=BISmark Wireless Measurements tool 
	URL:=http://doesnotexist.com
	DEPENDS:=+zlib +bismark-data-transmit 
endef

define Package/bismark-active-tmpfs/description
 This tool collects wireless traces in monitor mode. This tool is a part of infrastructure to understand wireless home networks.
endef

define Package/wifi-dump-tmpfs/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/wifi_dump $(1)/usr/bin/wifi_dump.bin
	$(INSTALL_BIN) ./files/etc/init.d/wifi_dump $(1)/etc/init.d/wifi_dump
	$(INSTALL_BIN) ./files/usr/bin/wifi_dump $(1)/usr/bin/wifi_dump
endef

 
define Package/wifi-dump-tmpfs/postinst
#!/bin/sh
#killall wifi_dump
#rm /var/run/wifi_dump.pid
start-stop-daemon -K -q -p /var/run/wifi_dump.pid -s TERM
/tmp/etc/init.d/wifi_dump restart
endef

define Package/wifi-dump-tmpfs/prerm
#!/bin/sh
/tmp/etc/init.d/wifi_dump stop
endef

$(eval $(call BuildPackage,wifi-dump-tmpfs))
