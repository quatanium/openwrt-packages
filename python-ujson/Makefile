#
# Copyright (c) 2015 Quatanium Co., Ltd.
#
# Licensed under MIT.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=ujson
PKG_VERSION:=1.33
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).zip
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/u/ujson/
PKG_MD5SUM:=8148a2493fff78940feab1e11dc0a893

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/python-ujson
	SECTION:=lang-python
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=python-ujson
	URL:=https://pypi.python.org/pypi/ujson
	DEPENDS:=+python
endef

define Package/python-ujson/description
	Ultra fast JSON encoder and decoder for Python
endef

define Build/Compile
	$(call Build/Compile/PyMod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

define Package/python-ujson/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)/
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call BuildPackage,python-ujson))
