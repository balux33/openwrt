# SPDX-License-Identifier: GPL-2.0-only

include $(TOPDIR)/rules.mk

PKG_NAME:=firmware-utils
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL=$(PROJECT_GIT)/project/firmware-utils.git
PKG_SOURCE_DATE:=2024-01-23
PKG_SOURCE_VERSION:=335d063cff23631050e6629f1dc692101f6df99d
PKG_MIRROR_HASH:=c85ad0d4522b04ee5a02202e63fd0bcb8d1676a63498a113669a268ba7abfa61

PKG_BUILD_DEPENDS:=openssl zlib

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/default
  SECTION:=utils
  CATEGORY:=Base system
  TITLE:=Firmware utility $(1)
  DEPENDS:=$(2)
endef

Package/oseama = $(call Package/default,oseama,@TARGET_bcm53xx)

define Package/oseama/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/oseama $(1)/usr/bin/
endef

Package/otrx = $(call Package/default,otrx,@(TARGET_bcm47xx||TARGET_bcm53xx))

define Package/otrx/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/otrx $(1)/usr/bin/
endef

$(eval $(call BuildPackage,oseama))
$(eval $(call BuildPackage,otrx))
