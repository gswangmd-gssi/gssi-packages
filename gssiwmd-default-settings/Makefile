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

define Package/gssiwmd-default-settings
  SECTION:=luci
  CATEGORY:=LuCI
  TITLE:=LuCI support for GSSIWMD Settings
  PKGARCH:=all
  DEPENDS:=+luci-base +luci +@LUCI_LANG_zh-cn
endef

define Package/gssiwmd-default-settings/description
	Language Support Packages.
endef

define Build/Compile
endef

define Package/gssiwmd-default-settings/install
	$(INSTALL_DIR) $(1)/etc/uci-defaults
	$(INSTALL_BIN) ./files/zzz-default-settings $(1)/etc/uci-defaults/99-default-settings
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci/i18n
	po2lmo ./po/zh-cn/default.po $(1)/usr/lib/lua/luci/i18n/default.zh-cn.lmo
	$(INSTALL_DIR) $(1)/etc/profile.d
	$(INSTALL_BIN) ./files/sysinfo.sh $(1)/etc/profile.d/sysinfo.sh
endef

$(eval $(call BuildPackage,gssiwmd-default-settings))
