#
# Copyright (C) 2011-2015 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

all: .done

.done:
	patch -d $(TOP) -p3 -i $(CURDIR)/fix-path.patch
	rm -f ../../../openwrt_chaos_calmer_entware/feeds/packages/net/iodine/patches/100-musl-compatibility.patch
	cp -f ./S19iodined ../../../openwrt_chaos_calmer_entware/feeds/packages/net/iodine/files/
	@touch $@

clean:
	@rm -f .done

.PHONY: clean
