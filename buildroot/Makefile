#
# Copyright (C) 2011-2015 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

export TOP?=$(shell (cd ../.. && pwd -P))
include ../config.mk

all: .buildroot_prepared

.buildroot_prepared: $(TOP)/downloads/openwrt_chaos_calmer_entware-r$(OPENWRT_REVISION)
	if [ ! -d "$(TOP)/openwrt_chaos_calmer_entware" ]; \
	then \
	    mkdir $(TOP)/openwrt_chaos_calmer_entware; \
	    cp -fr $(TOP)/downloads/openwrt_chaos_calmer_entware-r$(OPENWRT_REVISION)/* $(TOP)/openwrt_chaos_calmer_entware; \
	fi
	@echo "Adding new targets..."
	cp -fr ./targets/* ../../openwrt_chaos_calmer_entware/target/linux
	@echo "Applying patches..."
	@for patch in `ls $(CURDIR)/patches/*.patch | sort`; do ( \
                patch -d $(TOP) -p3 -i $$patch; \
        ); done
	@echo "Adding custom config..."
	cp -f .config $(TOP)/openwrt_chaos_calmer_entware/.config
	@touch $@

$(TOP)/downloads/openwrt_chaos_calmer_entware-r$(OPENWRT_REVISION): \
	    $(TOP)/downloads
	git clone https://github.com/earthGavinLee/openwrt_chaos_calmer_entware.git $(TOP)/openwrt_chaos_calmer_entware
	cp -f feeds.conf $(TOP)/openwrt_chaos_calmer_entware
	(cd $(TOP)/openwrt_chaos_calmer_entware; \
	./scripts/feeds update; \
	./scripts/feeds install -a;)
	mkdir -p $(TOP)/downloads/openwrt_chaos_calmer_entware-r$(OPENWRT_REVISION)
	ln -sf $(TOP)/downloads $(TOP)/openwrt_chaos_calmer_entware/dl
	cp -fr $(TOP)/openwrt_chaos_calmer_entware/* $(TOP)/downloads/openwrt_chaos_calmer_entware-r$(OPENWRT_REVISION)

$(TOP)/downloads:
	[ -d "$(TOP)/downloads" ] || mkdir -p "$(TOP)/downloads"

clean:
	@rm -f .buildroot_prepared

cleanall: clean
	@rm -rf $(TOP)/openwrt_chaos_calmer_entware

.PHONY: clean cleanall all
