# Beam Ports Tree

This ports overlay provides versions of Erlang and Elixir, allowing users to pick
a specific version of each.

## Development

``` shell
poudreire jail -c -j 143amd64 -v 14.3-RELEASE -a amd64

poudriere ports -c
poudriere ports -c -f beam -m null -M /workspace/github/goetic/beam-ports -p beam
```

``` shell
poudriere bulk -j 143amd64 -O beam lang/erlang-28.0.1
```
