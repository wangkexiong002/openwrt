include $(TOPDIR)/rules.mk

PKG_NAME:=geph5-client
PKG_VERSION:=0.2.83
PKG_RELEASE:=1

PKG_SOURCE_URL:=https://codeload.github.com/geph-official/geph5/tar.gz/refs/tags/geph5-client-v$(PKG_VERSION)?
PKG_SOURCE:=geph5-client-v$(PKG_VERSION).tar.gz
PKG_SOURCE_SUBDIR:=geph5-geph5-client-v$(PKG_VERSION)
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_SOURCE_SUBDIR)
PKG_MD5SUM:=facbd35212ab7b7831e53f97673c0ff3

PKG_BUILD_DEPENDS:=rust/host
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/rust/rust-package.mk

define Package/geph5-client
	SECTION:=net
	CATEGORY:=Network
	TITLE:=Geph5 client
endef

define Package/geph5-client/description
	Geph is a cross-platform, open-source transparent tunneling system designed to be secure and censorship-resistant.
endef

define Build/Compile
	$(call Build/Compile/Cargo,./binaries/geph5-client)
endef

define Package/geph5-client/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/target/*/release/geph5-client $(1)/usr/bin/
	$(INSTALL_CONF) ./files/geph5.yaml $(1)/etc/config/geph5.yaml
endef

$(eval $(call RustBinPackage,geph5-client))
$(eval $(call BuildPackage,geph5-client))
