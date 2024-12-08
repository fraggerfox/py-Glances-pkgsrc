# $NetBSD: Makefile,v 1.33 2024/11/02 02:47:21 fox Exp $

DISTNAME=	glances-4.2.1
PKGNAME=	${PYPKGPREFIX}-${DISTNAME:S/g/G/}
CATEGORIES=	sysutils python
MASTER_SITES=	${MASTER_SITE_PYPI:=g/glances/}

MAINTAINER=	fox@NetBSD.org
HOMEPAGE=	https://nicolargo.github.io/glances/
COMMENT=	Cross-platform curses-based monitoring tool
LICENSE=	gnu-lgpl-v3

TOOL_DEPENDS+=	${PYPKGPREFIX}-wheel>=0:../../devel/py-wheel
DEPENDS+=	${PYPKGPREFIX}-psutil>=5.6.7:../../sysutils/py-psutil
DEPENDS+=	${PYPKGPREFIX}-defusedxml-[0-9]*:../../textproc/py-defusedxml
DEPENDS+=	${PYPKGPREFIX}-packaging-[0-9]*:../../devel/py-packaging
DEPENDS+=	${PYPKGPREFIX}-orjson>=0:../../textproc/py-orjson

USE_LANGUAGES=	# none

PYTHON_VERSIONS_INCOMPATIBLE=	27
WHEEL_NAME=	Glances-${PKGVERSION_NOREV}

SUBST_CLASSES+=		prefix
SUBST_STAGE.prefix=	pre-configure
SUBST_MESSAGE.prefix=	Set correct prefix in setup.py
SUBST_FILES.prefix=	pyproject.toml
SUBST_SED.prefix=	-e 's,share/man,${PKGMANDIR},'

post-extract:
	# Removes the nodejs component which is not required.
	${RM} -fR ${WRKSRC}/glances/outputs/static

post-install:
	# remove pycache below pycache
	${RM} -f ${DESTDIR}${PREFIX}/${PYSITELIB}/glances/plugins/__pycache__/__pycache__/*
	${RMDIR} ${DESTDIR}${PREFIX}/${PYSITELIB}/glances/plugins/__pycache__/__pycache__/
	cd ${DESTDIR}${PREFIX} && \
	${MV} bin/glances bin/glances-${PYVERSSUFFIX} && \
	${MV} ${PKGMANDIR}/man1/glances.1 ${PKGMANDIR}/man1/glances-${PYVERSSUFFIX}.1 && \
	${MV} share/doc/glances share/doc/glances-${PYVERSSUFFIX}

.include "../../lang/python/batteries-included.mk"
.include "../../lang/python/wheel.mk"
.include "../../mk/bsd.pkg.mk"
