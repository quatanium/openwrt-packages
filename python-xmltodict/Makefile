#
# Copyright (c) 2015 Quatanium Co., Ltd.
#
# Licensed under MIT.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=xmltodict
PKG_VERSION:=0.9.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/x/xmltodict/
PKG_MD5SUM:=3dee8f1a5172315119051a3854596244
PKG_BUILD_DEPENDS:=python

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/python-xmltodict
	SECTION:=lang-python
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=python-xmltodict
	URL:=https://pypi.python.org/pypi/xmltodict
	DEPENDS:=+python
endef

define Package/python-xmltodict/description
	Makes working with XML feel like you are working with JSON
endef

define Build/Compile
	$(call Build/Compile/PyMod,, \
		install --prefix=/usr --root=$(PKG_INSTALL_DIR),\
		PYTHONPATH=$(PYTHON_LIB_DIR):$(STAGING_DIR_ROOT)/$(PYTHON_PKG_DIR); \
		)
endef

define Package/python-xmltodict/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)/
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call BuildPackage,python-xmltodict))
