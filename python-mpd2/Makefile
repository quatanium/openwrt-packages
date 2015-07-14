#
# Copyright (c) 2015 Quatanium Co., Ltd.
#
# Licensed under MIT.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-mpd2
PKG_VERSION:=0.5.4
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://pypi.python.org/packages/source/p/$(PKG_NAME)/
PKG_MD5SUM:=d891c3313011dbc6b294c2abf8b87da6
PKG_BUILD_DIR:=$(BUILD_DIR_HOST)/$(PKG_NAME)-$(PKG_VERSION)/
PKG_BUILD_DEPENDS:=python

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/python-mpd2
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Python-mpd2
  URL:=http://pypi.python.org/pypi/python-mpd2
endef

define Package/python-mpd2/description
	*python-mpd2* is a Python library which provides a client interface for \
		the `Music Player Daemon <http://musicpd.org>`__.
endef

define Build/Compile
	$(call Build/Compile/PyMod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

define Package/python-mpd2/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
	    $(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call BuildPackage,python-mpd2))
