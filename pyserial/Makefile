#
# Copyright (c) 2015 Quatanium Co., Ltd.
#
# Based on copyright (C) 2008-2011 openwrt
#
# This is free software, licensed under the GNU General Public License v2.
# License: http://www.gnu.org/licenses/gpl.html GPL version v2.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=pyserial
PKG_VERSION:=2.7
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/p/pyserial/
PKG_MD5SUM:=794506184df83ef2290de0d18803dd11

PKG_BUILD_DEPENDS:=python

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/pyserial
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=pyserial
  URL:=http://pyserial.sourceforge.net
  DEPENDS:=+python-mini
endef

define Package/pyserial/description
	serial port python bindings
endef

define Build/Compile
	$(call Build/Compile/PyMod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
	)
endef

define Package/pyserial/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
	    $(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call BuildPackage,pyserial))
