#
# Copyright (c) 2015 Quatanium Co., Ltd.
#
# Licensed under MIT.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=subprocess32
PKG_VERSION:=3.2.6
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://pypi.python.org/packages/source/s/subprocess32/
PKG_MD5SUM:=754c5ab9f533e764f931136974b618f1

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/python-subprocess32
	SECTION:=lang-python
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=python-subprocess32
	URL:=https://code.google.com/p/python-subprocess32/
	DEPENDS:=+python
endef

define Package/python-subprocess32/description
	Backport of the subprocess module from Python 3.2/3.3 for use on 2.x.
endef

define Build/Compile
	$(call Build/Compile/PyMod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

define Package/python-subprocess32/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)/
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call BuildPackage,python-subprocess32))
