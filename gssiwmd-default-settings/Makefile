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
  DEPENDS:=+luci-base +luci +@LUCI_LANG_zh-cn
endef

define Package/$(PKG_NAME)/description
	Language Support Packages.
endef

define Build/Compile
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/etc/uci-defaults
	$(INSTALL_BIN) ./files/zzz-default-settings $(1)/etc/uci-defaults/99-gssiwmd-default-settings
	
	# install README file
	$(INSTALL_DIR) $(1)/etc/readme
	cp ./files/README.md $(1)/etc/readme/README.md
	
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
