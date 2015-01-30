#
# Copyright (c) 2015 Quatanium Co., Ltd.
#
# Licensed under MIT.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=py-leveldb
PKG_REV:=68
PKG_VERSION:=$(PKG_REV)
PKG_RELEASE:=1

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://py-leveldb.googlecode.com/svn/trunk/
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_PROTO:=svn
PKG_SOURCE_VERSION:=$(PKG_REV)

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/python-leveldb
	SECTION:=lang-python
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=Python support for leveldb library
	URL:=https://code.google.com/p/py-leveldb/
	DEPENDS:=+python +libstdcpp
endef

define Package/python-leveldb/description
  Python wrapper for leveldb,
  A fast and lightweight key/value database library by Google.
endef

define Build/Prepare
	cd $(PKG_BUILD_DIR); \
		svn checkout http://snappy.googlecode.com/svn/trunk/ snappy-read-only; \
		git clone https://github.com/google/leveldb/ || (cd leveldb; git pull)
	$(call Build/Prepare/Default)
endef

define Build/Configure
	cd $(PKG_BUILD_DIR)/snappy-read-only; \
		./autogen.sh; \
		./configure \
			--enable-shared=no \
			--enable-static=yes \
			--host=mips-openwrt-linux-uclibc
endef

define Build/Compile
	cd $(PKG_BUILD_DIR)/snappy-read-only; \
		$(MAKE) clean; \
		$(MAKE) CXXFLAGS='-g -O2 -fPIC'
	cd $(PKG_BUILD_DIR)/leveldb; \
		$(MAKE) clean; \
		$(MAKE) libleveldb.a \
			CXX='mips-openwrt-linux-uclibc-gcc' \
			LDFLAGS='-L../snappy-read-only/.libs/ -Bstatic -lsnappy' \
			OPT='-fPIC -O2 -DNDEBUG -DSNAPPY -I../snappy-read-only' \
			SNAPPY_CFLAGS=''
	$(call Build/Compile/PyMod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

define Package/python-leveldb/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)/
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call BuildPackage,python-leveldb))
