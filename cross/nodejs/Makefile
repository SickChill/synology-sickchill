PKG_NAME = nodejs
PKG_VERS = v10.15.3
PKG_EXT = tar.gz
PKG_DIST_NAME = node-$(PKG_VERS).$(PKG_EXT)
PKG_DIST_SITE = https://nodejs.org/dist/$(PKG_VERS)
PKG_DIR = node-$(PKG_VERS)

UNSUPPORTED_ARCHS = $(ARMv5_ARCHS) $(ARMv7L_ARCHS) $(PPC_ARCHS)

HOMEPAGE = https://www.nodejs.org
COMMENT  = A JavaScript runtime built on Chrome\'s V8 JavaScript engine.
LICENSE  = https://github.com/nodejs/node/raw/master/LICENSE

CONFIGURE_ARGS = --cross-compiling --dest-os=linux --prefix=$(INSTALL_PREFIX)

include ../../mk/spksrc.cross-cc.mk

ifeq ($(findstring $(ARCH),$(ARMv5_ARCHS)),$(ARCH))
ENV += CC_host="gcc -m32"
ENV += CXX_host="g++ -m32"
CONFIGURE_ARGS += --dest-cpu=arm
endif

ifeq ($(findstring $(ARCH),$(ARMv7_ARCHS) $(ARMv7L_ARCHS)),$(ARCH))
ENV += CC_host="gcc -m32"
ENV += CXX_host="g++ -m32"
CONFIGURE_ARGS += --dest-cpu=arm
endif

ifeq ($(findstring $(ARCH),$(ARMv8_ARCHS)),$(ARCH))
ENV += CC_host=gcc
ENV += CXX_host=g++
CONFIGURE_ARGS += --dest-cpu=arm64
endif

ifeq ($(findstring $(ARCH),$(i686_ARCHS)),$(ARCH))
ENV += CC_host="gcc -m32"
ENV += CXX_host="g++ -m32"
CONFIGURE_ARGS += --dest-cpu=x86
endif

ifeq ($(findstring $(ARCH),$(x64_ARCHS)),$(ARCH))
ENV += CC_host=gcc
ENV += CXX_host=g++
CONFIGURE_ARGS += --dest-cpu=x86_64 --openssl-no-asm
endif

ifeq ($(findstring $(ARCH),$(PPC_ARCHS)),$(ARCH))
ENV += CC_host="gcc -m32"
ENV += CXX_host="g++ -m32"
CONFIGURE_ARGS += --dest-cpu=ppc
endif
