# termux-tools (metaharmonix edition)

Fork of [termux/termux-tools](https://github.com/termux/termux-tools) for the
**metaharmonix** phone runtime — a stripped-to-the-bone Termux variant
shipped with `notorch` and `aml` (the Arianna Method language) preinstalled,
aimed at on-device training and inference rather than general-purpose
mobile shell use.

This repository keeps the original tool surface (`termux-info`, `pkg`,
`login`, `chsh`, the `motd*` family, etc.) so packaging contracts with
`termux-app` and `termux-packages` stay intact. What changes here is
identity, defaults, and a small amount of integration with the
metaharmonix runtime:

* MOTDs greet the user as a metaharmonix shell, not a generic Termux one.
* `termux-info` reports presence and versions of `notorch`, `aml`, and the
  active `BLAS` backend — the things that actually matter for on-device
  training.
* Documentation pointers go to the metaharmonix umbrella, not termux.dev.

Everything else (script names, install paths, autotools build) is
deliberately left untouched in this first pass — see the umbrella repo
[`ariannamethod/metaharmonix`](https://github.com/ariannamethod/metaharmonix)
for the wider stripping plan.

## Mirrors

The `mirrors/` directory keeps the upstream Termux mirror set unchanged for
now. metaharmonix will publish its own mirror entries here once the package
build infrastructure (`termux-packages` fork) is wired up.

## Build

```
./autogen.sh
./configure --prefix=/data/data/com.termux/files/usr
make
make install
```

## License

GPLv3, inherited from upstream termux-tools. See `COPYING`.
