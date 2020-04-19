#
# Copyright (C) 2007-2020 Nicolas Massé
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libatomicops
PKG_VERSION:=7.6.10
PKG_RELEASE:=1
PKG_SOURCE:=libatomic_ops-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/ivmai/libatomic_ops/releases/download/v$(PKG_VERSION)/
PKG_HASH:=587edf60817f56daf1e1ab38a4b3c729b8e846ff67b4f62a6157183708f099af
PKG_MAINTAINER:=Nicolas Massé <nicolas.masse@itix.fr>
PKG_LICENSE:=GPLv2

PKG_BUILD_DIR:=$(BUILD_DIR)/libatomic_ops-$(PKG_VERSION)

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/libatomicops
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=implementations for atomic memory update operations
  DEPENDS:=@!TARGET_avr32
  URL:=https://github.com/ivmai/libatomic_ops
endef

define Package/libatomicops/description
  Provides implementations for atomic memory update
  operations on a number of architectures. This allows
  direct use of these in reasonably portable code. Unlike
  earlier similar packages, this one explicitly considers
  memory barrier semantics, and allows the construction of
  code that involves minimum overhead across a variety of
  architectures.
endef

CONFIGURE_ARGS += \
	--enable-shared \
	--enable-static \

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/
	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include/
	$(CP) $(PKG_BUILD_DIR)/src/atomic_ops $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libatomic_ops*.a $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libatomicops))
