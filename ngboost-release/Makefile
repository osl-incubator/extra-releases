NGBOOST_VERSION:=0.3.12
ARGS:=

.PHONY: clone
clone: 
	rm -rf ngboost
	git clone git@github.com:stanfordmlgroup/ngboost.git


.ONESHELL:
.PHONY: checkout-tag
checkout-tag:
	cd ngboost
	git checkout .
	git checkout v${NGBOOST_VERSION}


.ONESHELL:
.PHONY: apply-patches
apply-patches:
	cd ngboost
	patch pyproject.toml ../patches/pyproject.toml.patch
	patch __init__.py ../patches/__init__.py.patch


.ONESHELL:
.PHONY: publish
publish:
	cd ngboost
	poetry build
	poetry publish ${ARGS}

.ONESHELL:
.PHONY: run-workflow
run-workflow: clone checkout-tag apply-patches publish
