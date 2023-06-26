# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2023 Jonas Jelonek

include $(TOPDIR)/rules.mk

PKG_NAME:=modbus-proxy-rs
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/jonasjelonek/modbus-proxy-rs.git
PKG_SOURCE_DATE:=2023-12-14
PKG_SOURCE_VERSION:=2d11794ac22150e07a7635382c56bbd689771105
PKG_MIRROR_HASH:=5884135223232162922a22f7d186c97bfccf91713a5ca847e7a86924071a4cd0

PKG_MAINTAINER:=Jonas Jelonek <jelonek.jonas@gmail.com>

PKG_BUILD_DEPENDS:=rust/host

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/rust/rust-package.mk

define Package/modbus-proxy-rs
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=modbus-proxy-rs - Modbus TCP/IP multiplexer
  DEPENDS:=$(RUST_ARCH_DEPENDS)
  URL:=https://github.com/tiagocoutinho/modbus-proxy-rs
endef

define Package/modbus-proxy-rs/description
  modbus-proxy-rs allows multiple Modbus TCP/IP clients to connect
  to one Modbus TCP/IP server that only allows one connection at a
  time (often the case with PV inverters).
endef

define Package/modbus-proxy-rs/install
	$(INSTALL_DIR) $(1)/usr/bin/ $(1)/etc/init.d/ 
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/bin/* $(1)/usr/bin/ 
	$(INSTALL_BIN) ./files/modbus-proxy-rs.init $(1)/etc/init.d/modbus-proxy-rs 
endef

$(eval $(call RustBinPackage,modbus-proxy-rs))
$(eval $(call BuildPackage,modbus-proxy-rs))
