#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
# Modofield for luci-app-adguardhome-wmd 
# Wangmingde 2022-05-01

include $(TOPDIR)/rules.mk

PKG_NAME:=adguardhome-wmd
PKG_VERSION:=0.107.8
PKG_RELEASE:=50

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=e73605c4c541c13aa36e6a5b114450d3113ceec4
PKG_SOURCE_URL:=https://github.com/AdguardTeam/AdGuardHome
PKG_MIRROR_HASH:=skip

PKG_LICENSE:=GPL-3.0-only
PKG_LICENSE_FILES:=LICENSE.txt
PKG_MAINTAINER:=Dobroslaw Kijowski <dobo90@gmail.com>

PKG_BUILD_DEPENDS:=golang/host node/host node-yarn/host
PKG_BUILD_PARALLEL:=1
PKG_USE_MIPS16:=0

GO_PKG:=github.com/AdguardTeam/AdGuardHome
GO_PKG_BUILD_PKG:=github.com/AdguardTeam/AdGuardHome

AGH_BUILD_TIME:=$(shell date -d @$(SOURCE_DATE_EPOCH) +%FT%TZ%z)
AGH_VERSION_PKG:=github.com/AdguardTeam/AdGuardHome/internal/version
GO_PKG_LDFLAGS_X:=$(AGH_VERSION_PKG).channel=release \
	$(AGH_VERSION_PKG).version=v$(PKG_VERSION) \
	$(AGH_VERSION_PKG).buildtime=$(AGH_BUILD_TIME) \
	$(AGH_VERSION_PKG).goarm=$(GO_ARM) \
	$(AGH_VERSION_PKG).gomips=$(GO_MIPS)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/golang/golang-package.mk

define Package/adguardhome-wmd
	SECTION:=net
	CATEGORY:=Network
	TITLE:=Network-wide ads and trackers blocking DNS server
	URL:=https://github.com/AdguardTeam/AdGuardHome
	DEPENDS:=$(GO_ARCH_DEPENDS) +ca-bundle
endef

define Package/adguardhome-wmd/conffiles
/etc/adguardhome.yaml
/etc/config/adguardhome
endef

define Package/adguardhome-wmd/description
Free and open source, powerful network-wide ads and trackers blocking DNS server.
endef

define Build/Compile
	( \
		pushd $(PKG_BUILD_DIR) ; \
		make js-deps js-build ; \
		popd ; \
		$(call GoPackage/Build/Compile) ; \
	)
endef

define Package/adguardhome-wmd/install
	$(call GoPackage/Package/Install/Bin,$(1))
endef

$(eval $(call GoBinPackage,adguardhome-wmd))
$(eval $(call BuildPackage,adguardhome-wmd))
