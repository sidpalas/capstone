GITHUB_TOKEN := $(shell gh auth token)

# notes:
#	- current config results in go/api-golang service being "changed" since that is what PR #10 represents (as specified in event.json)
# - used catthehacker/ubuntu:act-22.04 because node:16-buster-slim doesnt contain git, and 24.04 image is still beta (and failed)
trigger-workflow:
	act pull_request \
		--container-architecture linux/amd64 \
		-s GITHUB_TOKEN="$(GITHUB_TOKEN)" \
		-e ${PWD}/event.json \
		-P ubuntu-24.04=catthehacker/ubuntu:act-22.04 \
		--directory ../../../.. \
		-W .github/workflows/test.yaml
