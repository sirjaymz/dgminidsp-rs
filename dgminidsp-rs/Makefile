## MIT LICENSE

include $(TOPDIR)/rules.mk

PKG_NAME:=dgminidsp-rs
PKG_VERSION:=0.1.12
PKG_RELEASE:=3

PKG_BUILD_DIR:=$(BUILD_DIR)/dgminidsp-rs-$(PKG_VERSION)-$(PKG_RELEASE)
PKG_SOURCE:=minidsp-rs-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/mrene/minidsp-rs/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=2ab458800db532e3e3d28255ff58e6a6f3a985778970bc07ca172611b775dd18

PKG_MAINTAINER:=James Jones <sirjaymz@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_URL:=https://github.com/sirjaymz/dgminidsp-rs
PKG_BUILD_DEPENDS:=rust/host
## PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/rust/rust-package.mk
## include $(TOPDIR)/feeds/packages/lang/rust/rust-values.mk

CARGO_HOME:= $(STAGING_DIR_HOST)/.cargo
RUSTFLAGS="-C linker=$(TARGET_CC_NOCACHE) -C ar=$(TARGET_AR)"
CONFIGURE_VARS += CARGO_HOME=$(CARGO_HOME) RUSTFLAGS=$(RUSTFLAGS)


##  define Build/Compile
##   cd $(PKG_BUILD_DIR) && \
##   $(CONFIGURE_VARS) cargo build --release --target=$(REAL_GNU_TARGET_NAME)
## endef

define Package/dgminidsp-rs
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=minidsp-rs for minidsp WIDG device
  DEPENDS:=$(RUST_ARCH_DEPENDS)
  URL:=https://github.com/sirjaymz/dgminidsp-rs
endef

define Package/dgminidsp-rs/description
  dgminidsp-rs is an openwrt package of minidsp-rs compiled explicitly for the minidsp WI-DG device using mipsel for the Mediatek 7688 chipset
endef

define Build/Compile
  $(call Build/Compile/Cargo,,)
endef

## Below is from mrene/minidsp-rs build instructions. need to mod above couple of lines to integrate
## "cargo build --release --bin minidsp"
## # The binary will then available as target/release/minidsp




## define Package/dgminidsp-rs/conffiles
## /etc/minidsp/config.toml
## endef

## define Package/dgminidsp-rs/install
## 	$(INSTALL_DIR) $(1)/usr/bin
##  	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/bin/procs $(1)/usr/bin/
##  	$(INSTALL_DIR) $(1)/etc/minidsp
##  	$(INSTALL_CONF) ./files/etc/minidsp/config.toml $(1)/etc/minidsp/
## endef

## ifneq ($(CONFIG_USE_MUSL),)
##  TARGET_CFLAGS += -D_LARGEFILE64_SOURCE
## endif

$(eval $(call RustBinPackage,dgminidsp-rs))
$(eval $(call BuildPackage,dgminidsp-rs))