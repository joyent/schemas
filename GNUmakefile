#
# Copyright (c) 2015, Joyent, Inc. All rights reserved.
#

#
# Files
#
JS_FILES	:= $(shell find lib test -name '*.js')
JSON_FILES	 = package.json
JSL_CONF_NODE	 = tools/jsl.node.conf
JSL_FILES_NODE	 = $(JS_FILES)
JSSTYLE_FILES	 = $(JS_FILES)
JSSTYLE_FLAGS	 = -f tools/jsstyle.conf

NODE		?= node
NPM		?= npm
TAPE	:= ./node_modules/.bin/tape

TESTS		 = \
	tst.cloudapi.js \
	tst.cnapi.js \
	tst.dapi.js \
	tst.manufacturing.js \
	tst.sdc.js \
	tst.vmapi.js

TESTFILES = $(TESTS:%=test/%)

include ./tools/mk/Makefile.defs

#
# Repo-specific targets
#
.PHONY: all
all:
	$(NPM) install

.PHONY: test
test: $(TESTFILES:%.js=%.tst)

%.tst: %.js $(TAPE)
	$(NODE) $<

$(TAPE):
	$(NPM) install

include ./tools/mk/Makefile.deps
include ./tools/mk/Makefile.targ
