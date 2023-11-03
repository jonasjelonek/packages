# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2023 Jonas Jelonek

include $(TOPDIR)/rules.mk

PKG_NAME:=ouch
PKG_VERSION:=0.4.2
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/ouch-org/ouch/tar.gz/$(PKG_VERSION)?
PKG_HASH:=08015fa92770515cfa00570bc5f0f0a4f28f0ad238f360f3579ac043723a6ec2

PKG_MAINTAINER:=Jonas Jelonek <jelonek.jonas@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=rust/host
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk
include ../../lang/rust/rust-package.mk

define Package/ouch
  SECTION:=utils
  CATEGORY:=Utilities
  SUBMENU:=Compression
  TITLE:=Obvious Unified Compression Helper
  DEPENDS:=$(RUST_ARCH_DEPENDS) +liblzma +libbz2 +zlib
  URL:=https://github.com/ouch-org/ouch
endef

define Package/ouch/description
  Painless compression and decompression in the terminal.
  Ouch (Obvious Unified Compression Helper) is a CLI tool for
  compression and decompression of various formats, e.g. tar, zip,
  gzip, zst, etc.
endef

$(eval $(call RustBinPackage,ouch))
$(eval $(call BuildPackage,ouch))
