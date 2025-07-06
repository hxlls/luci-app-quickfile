#
# Copyright (C) 2015-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v3.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=quickfile
PKG_VERSION:=1.0.0
PKG_RELEASE:=1

PKG_SOURCE:=quickfile-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/sbwml/luci-app-quickfile/releases/download/bin/
PKG_HASH:=747c9f50fee4a128bb8a0023c7a1ed80a32edf80884cfd972312b699f0aa0698

include $(INCLUDE_DIR)/package.mk

define Package/quickfile
	SECTION:=net
	CATEGORY:=Network
	SUBMENU:=Web Servers/Proxies
	TITLE:=Quick File Manager
	DEPENDS:=@(aarch64||x86_64)
	URL:=https://git.cooluc.com/sbwml/quickfile
endef

define Package/quickfile/description
  Lightweight web-based file manager for OpenWrt/LuCI with minimal resource usage.
endef

define Build/Compile
endef

define Package/quickfile/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/quickfile-$(ARCH_PACKAGES) $(1)/usr/bin/quickfile
	$(INSTALL_DIR) $(1)/etc/config $(1)/etc/init.d $(1)/etc/nginx/conf.d
	$(INSTALL_CONF) $(CURDIR)/files/quickfile.config $(1)/etc/config/quickfile
	$(INSTALL_BIN) $(CURDIR)/files/quickfile.init $(1)/etc/init.d/quickfile
	$(INSTALL_CONF) $(CURDIR)/files/quickfile.locations $(1)/etc/nginx/conf.d/quickfile.locations
endef

$(eval $(call BuildPackage,quickfile))
