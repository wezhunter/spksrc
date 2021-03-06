SPK_NAME = mantisbt
SPK_VERS = 1.2.17
SPK_REV = 2
SPK_ICON = src/mantisbt.png
DSM_UI_DIR = app

DEPENDS  = cross/$(SPK_NAME)

MAINTAINER = SynoCommunity
DESCRIPTION = Mantis is an easily deployable, web based bugtracker to aid product bug tracking. It requires PHP, MySQL and a web server. It is simpler than Bugzilla and easily editable.
DESCRIPTION_FRE = Mantis est un bugtracker web aisément déployable pour faciliter le suivi des bogues. Il nécessite PHP, MySQL et un serveur web. Il est plus simple d'accès que Bugzilla et facilement modifiable.
ADMIN_URL = /mantisbt/
RELOAD_UI = yes
STARTABLE = no
DISPLAY_NAME = MantisBT
CHANGELOG = "1. DSM 5.0 compatibility"

HOMEPAGE   = http://www.mantisbt.org/
LICENSE    = GPL

WIZARDS_DIR = src/wizard/
CONF_DIR = src/conf/

INSTALLER_SCRIPT = src/installer.sh
SSS_SCRIPT       = src/dsm-control.sh

INSTALL_DEP_SERVICES = apache-web mysql
START_DEP_SERVICES = apache-web mysql
INSTUNINST_RESTART_SERVICES = apache-web

INSTALL_PREFIX = /usr/local/$(SPK_NAME)

POST_STRIP_TARGET = mantisbt_extra_install

# Pure PHP package, make sure ARCH is not defined
override ARCH=

include ../../mk/spksrc.spk.mk

.PHONY: mantisbt_extra_install
mantisbt_extra_install:
	install -m 755 -d $(STAGING_DIR)/app
	install -m 644 src/app/config $(STAGING_DIR)/app/config
	install -m 644 src/config_inc.php $(STAGING_DIR)/share/$(SPK_NAME)/config_inc.php
	install -m 755 -d $(STAGING_DIR)/app/images
	for size in 16 24 32 48 72; do \
		convert $(SPK_ICON) -thumbnail $${size}x$${size} \
		        $(STAGING_DIR)/app/images/$(SPK_NAME)-$${size}.png ; \
	done
