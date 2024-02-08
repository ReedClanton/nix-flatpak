# `services.flatpak.enable`

## Description

Enables this Nix module.

## Default

```nix
false
```

## Example

```nix
true
```

# `services.flatpak.update.onActivation`

## Description

Enables flatpak updates at system activation. `false` so that repeated invocations of `nixos-rebuild` are idempotent. Applications pinned to a specific commit hash will not be updated.

## Default

```nix
false
```

## Example

```nix
true
```

# `services.flatpak.packages`

## Description

List of flatpak(s) user would like installed.

TODO: Figure out where flatpaks are pulled from that don't specify origin, then include that info here.

## Default

```nix
[]
```

## Example

```nix
[
    {
        appId = "io.github.nokse22.asciidraw";
        origin = "flathub";
    }
    {
        appId = "io.freetubeapp.FreeTube";
        origin = "flathub";
    }
]
```

# `services.flatpak.remotes`

## Description

List of remotes [`services.flatpak.packages`](TODO) will be installed from.

## Default

```nix
[
    {
        name = "flathub";
        location = "https://dl.flathub.org/repo/flathub.flatpakrepo";
    }
]
```

## Example

```nix
[
    {
        name = "flathub";
        location = "https://dl.flathub.org/repo/flathub.flatpakrepo";
    }
    {
        name = "flathub-beta";
        location = "https://flathub.org/beta-repo/flathub-beta.flatpakrepo";
    }
]
```

## **Warning**

As of 2024/02/08 adding a remote will remove the default remote. If a [package](TODO) can't be found in the provided remote(s), no warning or error will be shown.

# `services.flatpak.update`

## Description

Nix set that detemrines how updates will be handled.

# `services.flatpak.update.auto`

## Description

Nix set that determines if and how automated updates to flatpaks are applied.

# `services.flatpak.update.auto.enable`

## Description

Enables periodic updates. Auto updates *also* trigger on system activation.

## Default

```nix
false
```

## Example

```nix
true
```

## **Warning**

There's no need to also set [`services.flatpak.update.onActivation`](TODO) when this is set to `true`.

# `services.flatpak.update.auto.onCalendar`

## Description

Sets how frequently flatpaks are updated. Updates are scheduled by realtime systemd times, thus `onCalendar` accepts time in [systemd timers format](https://wiki.archlinux.org/title/systemd/Timers). For a list of systemd timer calendar event shorthand expressions, [see this](https://man.archlinux.org/man/systemd.time.7#CALENDAR_EVENTS).

## Default

```nix
"weekly"
```

## Example

```nix
"daily"
```

