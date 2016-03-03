#
# Copyright (C) 2011-2015 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

all: .done

.done:
	patch -d $(TOP) -p3 -i $(CURDIR)/fix-path.patch
	cp -f ./050-inotify_fix.patch ../../../openwrt_chaos_calmer_entware/feeds/packages/multimedia/minidlna/patches/
	cp -f ./060-conf_path.patch ../../../openwrt_chaos_calmer_entware/feeds/packages/multimedia/minidlna/patches/
	cp -f ./S90minidlna ../../../openwrt_chaos_calmer_entware/feeds/packages/multimedia/minidlna/files/
	@touch $@

clean:
	@rm -f .done

.PHONY: clean
