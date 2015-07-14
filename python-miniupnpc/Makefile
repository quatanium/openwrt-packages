#
# Copyright (c) 2015 Quatanium Co., Ltd.
#
# Based on copyright (C) 2010-2012 openwrt
#
# This is free software, licensed under the GNU General Public License v2.
# License: http://www.gnu.org/licenses/gpl.html GPL version v2.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=miniupnpc
PKG_VERSION:=1.9.20150206
PKG_RELEASE:=1

PKG_SOURCE_URL:=http://miniupnp.free.fr/files
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_MD5SUM:=96f3df608c28dbd5d2ad834f75dc61c9

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/python-miniupnpc
	SECTION:=lang-python
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=Python support for miniupnpc library
	URL:=http://miniupnp.free.fr/
	DEPENDS:=+python +libminiupnpc
endef

define Package/python-miniupnpc/description
  Python wrapper for miniupnpc.
  A MiniUPnP client library, which is useful whenever an application \
	 needs to listen for incomeing connections.
endef

TARGET_CFLAGS += $(FPIC)

MAKE_FLAGS += \
	OS="Linux" \

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/miniupnpc
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/include/miniupnpc/*.h \
		$(1)/usr/include/miniupnpc/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/*.{so*,a} \
		$(1)/usr/lib/
endef

define Build/Compile
	$(call Build/Compile/Default)
	$(call Build/Compile/PyMod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

define Package/python-miniupnpc/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)/
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call BuildPackage,python-miniupnpc))
