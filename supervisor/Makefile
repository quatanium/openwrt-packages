#
# Copyright (c) 2015 Quatanium Co., Ltd.
#
# Licensed under MIT.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=supervisor
PKG_VERSION:=3.1.3
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/s/supervisor/
PKG_MD5SUM:=aad263c4fbc070de63dd354864d5e552
PKG_BUILD_DEPENDS:=python python-setuptools

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/supervisor
	SECTION:=lang-python
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=supervisor
	URL:=https://pypi.python.org/pypi/supervisor
	DEPENDS:=+python python-meld3
endef

define Package/supervisor/description
	Supervisor is a client/server system that allows its users to \
		control a number of processes on UNIX-like operating systems.
endef

define Build/Compile
	$(call Build/Compile/PyMod,, \
		install --prefix=/usr --root=$(PKG_INSTALL_DIR), \
		PYTHONPATH="$(PYTHON_LIB_DIR):$(STAGING_DIR_ROOT)/$(PYTHON_PKG_DIR)"; \
		)
endef

define Package/supervisor/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)/
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)/
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/* \
		$(1)/usr/
	$(SED) '1s/#\!.*/#\!\/usr\/bin\/python/' $(1)/usr/bin/*
	$(INSTALL_DIR) $(1)/etc
	$(INSTALL_DATA) ./files/supervisord.conf $(1)/etc/supervisord.conf
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_DATA) ./files/supervisord.init $(1)/etc/init.d/supervisord
endef

define Package/superivosr/conffiles
	/etc/supervisord.conf
endef

$(eval $(call BuildPackage,supervisor))
