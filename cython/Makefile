#
# Copyright (c) 2015 Quatanium Co., Ltd.
#
# Based on copyright (C) 2008-2010 openwrt
#
# This is free software, licensed under the GNU General Public License v2.
# License: http://www.gnu.org/licenses/gpl.html GPL version v2.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=Cython
PKG_VERSION:=0.23.1
PKG_RELEASE:=1

PKG_SOURCE:=Cython-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://pypi.python.org/packages/source/C/$(PKG_NAME)/
PKG_MD5SUM:=db3c5b365e1c3f71c7cd90e96473a3ab
PKG_BUILD_DIR:=$(BUILD_DIR_HOST)/$(PKG_NAME)-$(PKG_VERSION)/

PKG_BUILD_DEPENDS:=python

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/cython
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=cython
  URL:=http://www.cython.org
  DEPENDS:=+python-mini
endef

define Package/cython/description
  Cython is a language that should make writing C extensions for the Python language easier
endef

define Build/Compile
	$(call Build/Compile/PyMod,,install --no-cython-compile --prefix="$(PKG_INSTALL_DIR)/usr") 
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
	    $(1)$(PYTHON_PKG_DIR)
endef

$(eval $(call BuildPackage,cython))
