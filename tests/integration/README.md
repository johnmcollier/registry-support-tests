# Devfile Registry Integration Tests

This folder contains the integration tests for the OCI-based Devfile Registry. The tests can be run against either a remote devfile registry (such as https://registry.stage.devfile.io), or a local devfile registry running your machine (such as in Minikube, or Docker Desktop).

## Build

The integration tests can be built to either run on your machine, or in a Docker container.

To build the test binary locally, run: `./build.sh`

To build the test binary docker image, run `./docker-build.sh`

## Run Locally

To run the tests locally, you must make sure that the CLI version of the `registry-library` is built and exists on your system path, as the integration tests rely on it. To do that:

1. Navigate to the `registry-library/` directory in the root of this repository
2. Run the `build.sh` script in that folder
3. Run `cp registry-library /usr/local/bin/registry-library` to add it to your system path

Then, to run the tests, navigate back to the `tests/integration` folder and run `./devfile-registry-integration` to run the tests

## Run in a Container

To run the tests in a container, simply run:
```
$ docker run --env REGISTRY=$REGISTRY devfile-registry-integration
```

Where `$REGISTRY` is the hostname of the devfile registry that you wish to test against (such as https://registry.devfile.io or http://devfile-registry-default.10.101.108.46.nip.io)