#
# Copyright (C) 2011-2015 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

all: .done

.done:
	patch -d $(TOP) -p3 -i $(CURDIR)/fix-path.patch
	cp -f ./S08samba ../../../openwrt_chaos_calmer_entware/package/network/services/samba36/files/
	@touch $@

clean:
	@rm -f .done

.PHONY: clean
