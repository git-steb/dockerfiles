# Dockerfiles to build RcppOctave on Travis-CI

The files here can be used to locally run tests of packages that simultaneously require R and Octave installations of different versions for testing.

The file [`travis/.travis.yml`](travis/.travis.yml), if put into the root of a repository, shows how to use layered docker images for Travis-CI builds. For an example, see [`@git-steb/RcppOctave/docker-setup`](https://github.com/git-steb/RcppOctave/tree/docker-setup) and the corresponding [`travis output`](https://travis-ci.org/git-steb/RcppOctave/builds/248898016).
