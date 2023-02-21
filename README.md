# Postgres backup and restore docker images

## Image origin

FORKED FROM: https://github.com/avencera/postgres-backup-restore that was FORKED FROM: https://github.com/schickling/dockerfiles/

## Usage in the PDS

Remember that this is a public repo.
We are using only `backup` image in our infrastructure. The `restore` image is supposed to be
used only in extraordinary situation.
In order to get a new `backup` image to the PDS infrastructure, you have to
locally build a docker image and push it to a `postgres-backup-restore` 
image repository. Please use `backup-<SHORT SHA>` tag. The `<SHORT SHA>` is a short SHA
hash of the master commit, from which the image was built.

