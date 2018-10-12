# $FreeBSD$

PORTNAME=	libsignon-glib
PORTVERSION=	2.0
CATEGORIES=	net-im
DIST_SUBDIR=	KDE/${GL_ACCOUNT}

MAINTAINER=	kde@FreeBSD.org
COMMENT=	GLib-based client library for applications handling account authentication

LICENSE=	LGPL21
LICENSE_FILE=	${WRKSRC}/COPYING

BUILD_DEPENDS=	vapigen:lang/vala \
		gtkdocize:textproc/gtk-doc

USES=		gnome libtool meson pkgconfig python
USE_GNOME=	introspection pygobject3
USE_PYTHON=	py3kplist
USE_GITLAB=	yes
GL_ACCOUNT=	accounts-sso
GL_COMMIT=	80e08a8045d2e91f0c460c94d0356d471b0f8178
GL_TUPLE=	accounts-sso:signon-dbus-specification:67487954653006ebd0743188342df65342dc8f9b:dbus/libsignon-glib/interfaces

BINARY_ALIAS=	python=python${PYTHON_VER}

OPTIONS_DEFINE=	TEST

TEST_DEPENDS=		checkmk:devel/check
TEST_TEST_TARGET=	check
TEST_MESON_TRUE=	tests

post-install:
	${PYTHON_CMD} ${PYTHON_LIBDIR}/compileall.py \
		-f -d ${PYTHONPREFIX_SITELIBDIR}/gi/overrides \
		${STAGEDIR}${PYTHONPREFIX_SITELIBDIR}/gi/overrides
	${PYTHON_CMD} -O ${PYTHON_LIBDIR}/compileall.py \
		-f -d ${PYTHONPREFIX_SITELIBDIR}/gi/overrides \
		${STAGEDIR}${PYTHONPREFIX_SITELIBDIR}/gi/overrides

.include <bsd.port.mk>
