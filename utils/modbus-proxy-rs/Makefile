# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2023 Jonas Jelonek

include $(TOPDIR)/rules.mk

PKG_NAME:=modbus-proxy-rs
PKG_VERSION:=1.0.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/tiagocoutinho/modbus-proxy-rs/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=e00a5ec9acb15d651ba37e070ac6a15e4810e14c0bf140da2f79b88a2713abce

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
