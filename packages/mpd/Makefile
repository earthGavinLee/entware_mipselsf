#
# Copyright (C) 2011-2015 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

all: .done

.done:
	patch -d $(TOP) -p3 -i $(CURDIR)/fix-path.patch
	cp -f ./S89mpd ../../../openwrt_chaos_calmer_entware/feeds/packages/sound/mpd/files/
	@touch $@

clean:
	@rm -f .done

.PHONY: clean
