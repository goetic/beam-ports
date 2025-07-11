# Beam Ports Tree

This ports overlay provides versions of Erlang and Elixir, allowing users to pick
a specific version of each.

## Development

``` shell
poudreire jail -c -j 143amd64 -v 14.3-RELEASE -a amd64
poudreire jail -c -j 143aarch64 -v 14.3-RELEASE -a arm64.aarch64

poudriere ports -c
poudriere ports -c -f beam -m null -M /workspace/github/goetic/beam-ports -p beam
```

``` shell
poudriere bulk -j 143amd64 -O beam lang/erlang-28.0.1
```

``` shell
poudriere pkgclean -A -j <jail>
poudriere logclean -a -j <jail>
```
