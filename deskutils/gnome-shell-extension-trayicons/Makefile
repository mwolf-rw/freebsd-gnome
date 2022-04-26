PORTNAME=	gnome-shell-extension-trayicons
PORTVERSION=	23
DISTVERSIONPREFIX=	extensions.gnome.org-v
CATEGORIES=	deskutils gnome
DIST_SUBDIR=	gnome

MAINTAINER=	gnome@FreeBSD.org
COMMENT=	Tray icons for the top panel

LICENSE=	GPLv3
LICENSE_FILE=	${WRKSRC}/LICENSE

BUILD_DEPENDS=	gnome-shell>=3.28:x11/gnome-shell \
		gsettings-desktop-schemas>=3.12.0:devel/gsettings-desktop-schemas \
		sassc>0:textproc/sassc
RUN_DEPENDS=	gnome-shell>=3.28:x11/gnome-shell \
		gsettings-desktop-schemas>=3.12.0:devel/gsettings-desktop-schemas

USES=		gettext gmake gnome localbase pkgconfig
USE_GNOME=	glib20
USE_GITHUB=	yes

GLIB_SCHEMAS=	org.gnome.shell.extensions.trayIconsReloaded.gschema.xml

GH_ACCOUNT=	MartinPL
GH_PROJECT=	Tray-Icons-Reloaded
GH_TAGNAME=	${PORTVERSION}

PKGMESSAGE=	../gnome-shell-extra-extensions/pkg-message.slaves

NO_ARCH=	yes
NO_BUILD=	yes

do-install:
	@${MKDIR} ${STAGEDIR}${PREFIX}/share/glib-2.0/schemas/
	@${MKDIR} ${STAGEDIR}${PREFIX}/share/gnome-shell/extensions/trayIconsReloaded@selfmade.pl
	${INSTALL_DATA} ${WRKSRC}/schemas/${GLIB_SCHEMAS} \
		${STAGEDIR}${PREFIX}/share/glib-2.0/schemas/
	cd ${WRKSRC} && ${COPYTREE_SHARE} . \
		${STAGEDIR}${PREFIX}/share/gnome-shell/extensions/trayIconsReloaded@selfmade.pl
	@${FIND} ${STAGEDIR}${PREFIX} -name \*.po -delete

.include <bsd.port.mk>
