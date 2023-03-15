# PRERELEASE defines semver prerelease tag based on the state of the current git tree.
# For a clean tree this is simply short commit hash of HEAD, e.g., "4be01eb".
# Dirty tree has "-dirty" suffix added, e.g., "4be01eb-dirty".
PRERELEASE ?= $(shell git describe --match= --always --dirty)

# TAG for the postgres-backup-restore docker image, e.g., "backup-4be01eb-dirty".
IMG_TAG ?= backup-$(PRERELEASE)
IMG_REPO ?= docker.io

# Image URL to use all building/pushing image targets
IMG ?= $(IMG_REPO)/portworx/postgres-backup-restore:$(IMG_TAG)

.PHONY: docker-build docker-push

docker-build:
	docker build . -t ${IMG}

docker-push:
	docker push ${IMG}
