include $(TOPDIR)/rules.mk

PKG_NAME:=tuya_esp_daemon
PKG_VERSION:=1.0.0
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/MaksimDalgeda/tuya-esp-control.git
PKG_SOURCE_VERSION:=341f39ad872b2e0fec989ed594b6adb2b3d48e8c

PKG_MIRROR_HASH:=skip

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/tuya_esp_daemon
	CATEGORY:=Base system
	TITLE:=Tuya ESP Control Daemon
	DEPENDS:=+tuya_iot_core +cJSON +libubus +libubox +libblobmsg-json
endef

define Package/tuya_esp_daemon/description
	Tuya daemon for controlling ESP devices through UBUS
endef

define Build/Configure
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		CC="$(TARGET_CC)" \
		AR="$(TARGET_AR)" \
		STAGING_DIR="$(STAGING_DIR)" \
		TUYA_SDK="$(STAGING_DIR)/usr"
endef

define Package/tuya_esp_daemon/install
	$(INSTALL_DIR) $(1)/usr/bin

	$(INSTALL_BIN) \
		$(PKG_BUILD_DIR)/build/tuya-esp-daemon \
		$(1)/usr/bin/tuya-esp-daemon

	$(INSTALL_DIR) $(1)/etc/init.d

	$(INSTALL_BIN) \
		./files/etc/init.d/tuya-esp-daemon \
		$(1)/etc/init.d/tuya-esp-daemon
endef

$(eval $(call BuildPackage,tuya_esp_daemon))