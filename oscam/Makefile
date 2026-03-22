#
# Copyright (C) 2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=oscam
PKG_VERSION:=11945
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/gfto/oscam.git
PKG_SOURCE_VERSION:=6c8324e0
PKG_MIRROR_HASH:=skip

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/oscam
  SECTION:=utils
  CATEGORY:=Utilities
  DEPENDS:=+libopenssl +libpthread +libusb-1.0
  TITLE:=OSCam - Open Source Conditional Access Module
  URL:=https://git.streamboard.tv/common/oscam
endef

define Package/oscam/description
  OSCam is an Open Source Conditional Access Module software.
endef

CMAKE_OPTIONS += \
	-DCS_CONFDIR=/etc/config/oscam \
	-DWEBIF=1 \
	-DWITH_SSL=1 \
	-DWITH_LIBUSB=1

define Package/oscam/install
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/oscam.init $(1)/etc/init.d/oscam

	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/oscam $(1)/usr/bin/

	$(INSTALL_DIR) $(1)/etc/config/oscam
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/share/doc/oscam/example/* $(1)/etc/config/oscam/
endef

$(eval $(call BuildPackage,oscam))
