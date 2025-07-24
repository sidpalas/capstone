GITHUB_TOKEN := $(shell gh auth token)

# Expects HONEYCOMB_OTLP_HEADERS to be defined in .secrets file
trigger-workflow:
	act workflow_run \
		--container-architecture linux/amd64 \
		-s GITHUB_TOKEN="$(GITHUB_TOKEN)" \
		-e ${PWD}/event.json \
		-P ubuntu-24.04=node:16-bullseye-slim \
		--directory ../../../.. \
		-W .github/workflows/export-timing-data.yaml
