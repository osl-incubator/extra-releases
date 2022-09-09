NGBOOST_VERSION:=0.3.12
ARGS:=

.PHONY: clone
clone: 
	rm -rf ngboost
	git clone git@github.com:stanfordmlgroup/ngboost.git


.ONESHELL:
.PHONY: checkout-tag
checkout-tag: clone
	cd ngboost
	git checkout .
	git checkout v${NGBOOST_VERSION}


.ONESHELL:
.PHONY: apply-patches
apply-patches: checkout-tag
	cd ngboost
	patch pyproject.toml ../patches/pyproject.toml.patch
	patch ngboost/__init__.py ../patches/__init__.py.patch


.ONESHELL:
.PHONY: publish
publish:
	cd ngboost
	poetry build
	poetry publish ${ARGS}

.ONESHELL:
.PHONY: run-workflow
run-workflow: apply-patches publish
