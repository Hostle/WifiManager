include $(TOPDIR)/rules.mk

PKG_NAME:=wifimanager
PKG_VERSION:=1.01.1

include $(INCLUDE_DIR)/package.mk

define Package/wifimanager/description
  Automated Wireless Configuration Daemon
endef

define Package/firewrt
  SECTION:=sys
  CATEGORY:=System
  TITLE:=WifiManager
endef

define Package/wifimanager/description
  Automated Wireless Configuration Daemon
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef


define Build/Configure
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
	CC="$(TARGET_CC)" \
	CFLAGS="$(TARGET_CFLAGS) -Wall -fPIC"
endef

define Package/firewrt/install
	$(INSTALL_DIR) $(1)/usr/lib/lua
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/wifimanager.so $(1)/usr/lib/lua/wifimanager.so
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) ./files/usr/bin/wifimanager $(1)/usr/bin/wifimanager
	$(INSTALL_DIR) $(1)/usr/lib/lua/WifiManager
	$(INSTALL_DATA) ./files/usr/lib/lua/WiFiManager/functions.lua $(1)/usr/lib/lua/WifiManager/functions.lua
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/etc/init.d/wifimanager $(1)/etc/init.d/wifimanager
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/etc/config/wifimanager $(1)/etc/config/wifimanager
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci/controller/admin
	$(INSTALL_DATA) ./files/usr/lib/lua/luci/controller/admin/wifimanager.lua $(1)/usr/lib/lua/luci/controller/admin/wifimanager.lua
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci/model/cbi/admin_wifimanager
	$(INSTALL_DATA) ./files/usr/lib/lua/luci/model/cbi/admin_wifimanager/* $(1)/usr/lib/lua/luci/model/cbi/admin_wifimanager/
endef

$(eval $(call BuildPackage,wifmanager))
