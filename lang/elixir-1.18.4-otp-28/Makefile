PORTNAME=	elixir
DISTVERSIONPREFIX=	v
DISTVERSION=	1.18.4
CATEGORIES=	lang
MASTER_SITES+=	https://github.com/elixir-lang/elixir/releases/download/${DISTVERSIONPREFIX}${PORTVERSION}/:doc
PKGNAMESUFFIX=	-1.18.4-otp-28
DISTFILES=	Docs.zip:doc
DIST_SUBDIR=	elixir/${PORTVERSION}

MAINTAINER=	admin@goetic.dev
COMMENT=	Functional, meta-programming aware language built on top of Erlang VM
WWW=		https://elixir-lang.org/

LICENSE=	APACHE20

BUILD_DEPENDS=	erlang-28.0.4>28:lang/erlang-28.0.4
# RUN_DEPENDS=	erlang-28*>28:lang/erlang-28*

USES=		gmake

USE_GITHUB=	yes
GH_ACCOUNT=	elixir-lang

CONFLICTS=	elixir-* # bin/elixir bin/elixirc bin/iex

USE_LOCALE=	en_US.UTF-8
ALL_TARGET=	# empty

REINPLACE_ARGS=	-i ""
NO_ARCH=	yes
MAKE_ENV+=	MAN_PREFIX=${PREFIX}/share/man \
		PATH="${LOCALBASE}/lib/erlang-28.0.4/bin:${PATH}"

OPTIONS_DEFINE=		DOCS
OPTIONS_SUB=		yes

.include <bsd.port.options.mk>

post-extract:
	@${FIND} ${WRKDIR}/doc -name .build -delete

post-install-DOCS-on:
	${MKDIR} ${STAGEDIR}${DOCSDIR}
	cd ${WRKDIR}/doc/ && ${COPYTREE_SHARE} \* ${STAGEDIR}${DOCSDIR}

post-install:
	${MKDIR} ${STAGEDIR}${PREFIX}/lib/elixir/lib
	cd ${WRKSRC}/lib/ && for lib in *; do \
		${MKDIR} ${STAGEDIR}${PREFIX}/lib/elixir/lib/$${lib}/lib; \
		cd ${WRKSRC}/lib/$${lib}/lib && \
			${COPYTREE_SHARE} \* ${STAGEDIR}${PREFIX}/lib/elixir/lib/$${lib}/lib; \
	done

do-test:
	cd ${WRKSRC} && ${SETENV} ${MAKE_ENV} ${MAKE_CMD} test

.include <bsd.port.mk>
