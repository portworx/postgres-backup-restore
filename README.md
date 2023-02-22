# Postgres backup and restore docker images

## Image origin

FORKED FROM: https://github.com/avencera/postgres-backup-restore that was FORKED FROM: https://github.com/schickling/dockerfiles/

## Usage in the PDS

Remember that this is a public repo.
We are using only `backup` image in our infrastructure. The `restore` image
is supposed to be used only occasionally (using the restore runbook).

### Building and pushing to the image registry

```shell
make docker-build

make docker-push
```

### Updating image in the infrastructure repository

For `backup` image only, after successful build and push, update the
image tag in the infrastructure repo (`backup-job.yaml` file).
