include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

NETWORK_DEVICES_MENU:=Network Devices

PKG_NAME:=e1000e
PKG_VERSION:=3.8.4

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://downloadmirror.intel.com/15817/eng/$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_HASH:=4696BBE30E959C5A1BD006BE066358FF5FE76464

PKG_MAINTAINER:=YourWildDad <053700@gmail.com>
PKG_LICENSE:=GPL-2.0-only

include $(INCLUDE_DIR)/package.mk

define KernelPackage/e1000e-new
  SUBMENU:=$(NETWORK_DEVICES_MENU)
  TITLE:=Intel(R) PRO/1000 PCIe cards kernel support $(PKG_VERSION)
  DEPENDS:=@PCIE_SUPPORT +kmod-ptp
  KCONFIG:=CONFIG_E1000E
  FILES:=$(PKG_BUILD_DIR)/e1000e.ko
  AUTOLOAD:=$(call AutoProbe,e1000e)
  MODPARAMS.e1000e:= \
    IntMode=1 \
    InterruptThrottleRate=4,4,4,4,4,4,4,4
endef

define KernelPackage/e1000e-new/description
 Kernel modules for Intel(R) PRO/1000 PCIe Ethernet adapters $(PKG_VERSION).
endef

MAKE_FLAGS += KERNEL_SRC=$(LINUX_DIR) ARCH=$(LINUX_KARCH)
MAKE_PATH:=kernelmod

$(eval $(call KernelPackage,e1000e-new))
