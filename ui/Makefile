
# Install bun
# https://bun.sh/docs/installation

.PHONY: build
build:
	rm -f bun.lockb
	bun install
	bun run build

.PHONY: clean
clean:
	rm -rf node_modules
	rm -f bun.lockb
	rm -rf dist
	rm -rf .bun
	rm -rf .cache

.PHONY: install-bun
install-bun:
	brew install bun

.PHONY: audit
audit:
	@echo "Running security audit..."
	bun audit
	@echo "Security audit completed."

.PHONY: build
update:
	@echo "Updating UI lock file..."
	npm audit fix
	bun install --frozen-lockfile --production
	@echo "Updating UI lock file done."

.PHONY: license-check
license-check: ## Check UI dependency licenses for compliance
	# LGPL-3.0-or-later is allowed for @img/sharp-libvips-* packages (used by Next.js image
	# optimization as native binary libraries; they are not modified and LGPL only requires
	# sharing modifications to the LGPL library itself, not the consuming code)
	npm run license-check