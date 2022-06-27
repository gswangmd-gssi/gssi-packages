#
# Copyright (C) 2016-2017 GitHub 
#
# This is free software, licensed under the GNU General Public License v3.
# See /LICENSE for more information.

include $(TOPDIR)/rules.mk

PKG_NAME:=gssiwmd-default-settings
PKG_VERSION:=2
PKG_RELEASE:=27
PKG_LICENSE:=GPLv3
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  SECTION:=luci
  CATEGORY:=LuCI
  TITLE:=LuCI support for GSSIWMD Settings
  PKGARCH:=all
  DEPENDS:=+luci-base
endef

define Package/$(PKG_NAME)/description
	Language Support Packages.
endef

define Build/Prepare
	chmod -R +x ./files/bin ./files/sbin ./files/etc/profile.d ./files/etc/rc.d ./files/usr/share target/*/{*,}/files/{etc/init.d,usr/bin} >/dev/null || true
endef

define Build/Compile
endef

define Package/$(PKG_NAME)/install
	$(CP) ./files/* $(1)/	
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
