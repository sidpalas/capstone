GITHUB_TOKEN := $(shell gh auth token)

# notes:
#	- --no-skip-checkout used to get git tags
# - used catthehacker/ubuntu:act-22.04 because node:16-buster-slim doesnt contain git, and 24.04 image is still beta (and failed)
trigger-workflow-workflow-dispatch:
	act workflow_dispatch \
		--container-architecture linux/amd64 \
		-s GITHUB_TOKEN="$(GITHUB_TOKEN)" \
		-e ${PWD}/workflow-dispatch-event.json \
		-P ubuntu-24.04=catthehacker/ubuntu:act-22.04 \
		--directory ../../../.. \
		--no-skip-checkout \
		-W .github/workflows/build-push.yaml

trigger-workflow-tag:
	act push \
		--container-architecture linux/amd64 \
		-s GITHUB_TOKEN="$(GITHUB_TOKEN)" \
		-e ${PWD}/push-tag-event.json \
		-P ubuntu-24.04=catthehacker/ubuntu:act-22.04 \
		--directory ../../../.. \
		--no-skip-checkout \
		-W .github/workflows/build-push.yaml
