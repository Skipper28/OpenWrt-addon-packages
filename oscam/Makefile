#
# Copyright (C) 2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=oscam
PKG_REV:=8625
PKG_VERSION:=$(PKG_REV)
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=svn
PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_SOURCE_SUBDIR).tar.bz2
PKG_SOURCE_URL:=http://streamboard.de.vu/svn/oscam/trunk

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/oscam
  SECTION:=utils
  CATEGORY:=Utilities
# DEFAULT:=y
  DEPENDS:=+libopenssl +libpthread +librt +libusb-1.0 +kmod-usb-serial +kmod-usb-serial-ftdi
  TITLE:=OSCam is an Open Source Conditional Access Module software
  URL:=http://streamboard.de.vu:8001/
endef

define Package/oscam/description
  OSCam is an Open Source Conditional Access Module Software
endef

CMAKE_OPTIONS += \
		-DCS_CONFDIR=/etc/config/oscam
CONFIGURE_ARGS += --with-ssl=openssl

define Package/oscam/install
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/oscam.init $(1)/etc/init.d/oscam

	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/oscam $(1)/usr/bin/

	$(INSTALL_DIR) $(1)/etc/config/oscam
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/share/doc/oscam/example/* $(1)/etc/config/oscam/

endef

$(eval $(call BuildPackage,oscam))
