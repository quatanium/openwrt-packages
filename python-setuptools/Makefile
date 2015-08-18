#
# Copyright (c) 2015 Quatanium Co., Ltd.
#
# Licensed under MIT.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=setuptools
PKG_VERSION:=18.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://pypi.python.org/packages/source/s/$(PKG_NAME)/
PKG_MD5SUM:=f72e87f34fbf07f299f6cb46256a0b06
PKG_BUILD_DIR:=$(BUILD_DIR_HOST)/$(PKG_NAME)-$(PKG_VERSION)/

HOST_BUILD_DEPENDS:=python

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

PYTHON:=$(HOST_PYTHON_BIN)

define Package/python-setuptools
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Python-setuptools
  URL:=http://pypi.python.org/pypi/python-setuptools
  DEPENDS:=+python
endef

define Package/python-setuptools/description
	Easily download, build, install, upgrade, and uninstall Python packages.
endef

define Host/Compile
	$(call Build/Compile/PyMod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

define Host/Install
	$(INSTALL_DIR) $(STAGING_DIR)$(PYTHON_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
	    $(STAGING_DIR)$(PYTHON_PKG_DIR)/
endef

define Build/Compile
	$(call Build/Compile/PyMod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

define Package/python-setuptools/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)/
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/bin/easy_install \
		$(1)/usr/bin/
	$(SED) '1s/#\!.*/#\!\/usr\/bin\/python/' $(1)/usr/bin/easy_install
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,python-setuptools))
