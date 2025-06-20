# SPDX-License-Identifier: GPL-3.0-only
#
# Copyright (C) 2021 ImmortalWrt.org

include $(TOPDIR)/rules.mk

PKG_NAME:=cloudflared
PKG_VERSION:=2025.6.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/cloudflare/cloudflared/tar.gz/$(PKG_VERSION)?
PKG_HASH:=5d1dc902930bca96b4d97d7204f6472c53ae04f523f55f2803e8115c99310912

PKG_LICENSE:=Apache-2.0
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Tianling Shen <cnsztl@immortalwrt.org>

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1
PKG_USE_MIPS16:=0

GO_PKG:=github.com/cloudflare/cloudflared
GO_PKG_LDFLAGS_X:=main.Version=$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include ../../lang/golang/golang-package.mk

define Package/cloudflared
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Web Servers/Proxies
  TITLE:=Cloudflare Tunnel client
  URL:=https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/install-and-setup/tunnel-guide
  DEPENDS:=$(GO_ARCH_DEPENDS) +ca-bundle
endef

define Package/cloudflared/description
  Contains the command-line client for Cloudflare Tunnel, a tunneling
  daemon that proxies traffic from the Cloudflare network to your origins.

  This daemon sits between Cloudflare network and your origin (e.g. a
  webserver). Cloudflare attracts client requests and sends them to you
  via this daemon, without requiring you to poke holes on your firewall
  --- your origin can remain as closed as possible.
endef

define Package/cloudflared/install
	$(call GoPackage/Package/Install/Bin,$(1))
endef

$(eval $(call GoBinPackage,cloudflared))
$(eval $(call BuildPackage,cloudflared))
