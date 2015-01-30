#
# Copyright (c) 2015 Quatanium Co., Ltd.
#
# Licensed under MIT.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=tzlocal
PKG_VERSION:=1.1.2
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).zip
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/t/tzlocal/
PKG_MD5SUM:=0ed82c55c4ab1463ffc74a792fda7e2b
PKG_BUILD_DEPENDS:=python python-setuptools

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/python-tzlocal
	SECTION:=lang-python
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=python-tzlocal
	URL:=https://pypi.python.org/pypi/tzlocal
	DEPENDS:=+python
endef

define Package/python-tzlocal/description
	tzinfo object for the local timezone
endef

define Build/Compile
	$(call Build/Compile/PyMod,., \
		install --prefix=/usr --root=$(PKG_INSTALL_DIR), \
		PYTHONPATH=$(PYTHON_LIB_DIR):$(STAGING_DIR_ROOT)/$(PYTHON_PKG_DIR); \
		)
endef

define Package/python-tzlocal/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)/
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call BuildPackage,python-tzlocal))
