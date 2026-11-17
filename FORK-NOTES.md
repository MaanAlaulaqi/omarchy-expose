# Personal Exposé fork

Source checkout: /home/rat/Work/packages/omarchy-expose

- origin: https://github.com/MaanAlaulaqi/omarchy-expose
- upstream: https://github.com/kristofferR/omarchy-expose
- Plugin identity: expose.window-overview (unchanged).
- Installed runtime: ~/.config/omarchy/plugins/expose.window-overview
- Shortcut: Super+O. Super+Shift+O remains pop-out/pin.

## New laptop

Install Omarchy, then install this fork (not both forks at once):

```bash
omarchy plugin add https://github.com/MaanAlaulaqi/omarchy-expose.git --enable
```

Add the following to ~/.config/hypr/bindings.lua after checking for conflicts:

```lua
o.rebind("SUPER + O", "Exposé", hl.dsp.event("expose.window-overview:toggle"))
o.rebind("SUPER + SHIFT + O", "Pop window out (float & pin)", "omarchy-hyprland-window-pop")
```

Run hyprctl reload and hyprctl configerrors. Plugin preferences in shell.json
are machine-local and are not carried by this source repository. Back them up
separately; do not replace a new laptop's complete shell.json blindly.

## Development

Work here rather than editing the installed runtime. Follow AGENTS.md for
validation, rollback refs, installation, shell restart, and live verification.
Run ./validate before installing a build. Keep origin pointed at the personal
fork and upstream at the original project. Review and merge upstream updates
explicitly; do not discard local feature work to match upstream.

The existing installed runtime still uses upstream as its origin. Switch that
runtime origin to the personal fork when deploying the first tested fork build,
so future plugin updates follow the personal fork.

Original AGENTS.md marketplace/release instructions describe the upstream
project's public release workflow. This personal fork does not automatically
publish a marketplace listing or update the original author's repositories.

## Planned monitor destinations

Keep window inclusion modes (all/this/each display) separate from the drag
 destination. Place monitor targets above the workspace strip. During a drag,
hover selects the destination monitor after a short delay; the workspace row
then displays that monitor's workspaces. Preserve selection while moving down.
Drop on a workspace to move there; drop on a monitor to use its active workspace.
Hover alone never moves a window. Escape cancels. Preserve current single-screen
behavior and existing settings. Implement and test this as a cohesive change,
including settings labels, before deploying it.
