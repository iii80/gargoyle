# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=nftables
PKG_VERSION:=0.8.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=https://netfilter.org/projects/$(PKG_NAME)/files
PKG_HASH:=8aead66cce70d68c70e4be917813abcbcf62811ee6de4c7761d0e34391772fc4
PKG_MAINTAINER:=Steven Barth <steven@midlink.org>
PKG_LICENSE:=GPL-2.0

PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk

DISABLE_NLS:=

CONFIGURE_ARGS += \
        --with-mini-gmp \
        --without-cli \

define Package/nftables
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Firewall
  TITLE:=nftables packet filtering userspace utility
  DEPENDS:=+kmod-nft-core +libnftnl
  URL:=http://netfilter.org/projects/nftables/
endef

define Package/nftables/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(CP) $(PKG_BUILD_DIR)/src/nft $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,nftables))
