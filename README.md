# VIVE Charge Dock

VIVE Charge Dock is an umbrella project for a charging system for original
HTC VIVE controllers. The electrical and mechanical parts are maintained as
separate repositories and included here as Git submodules.

This repository records a known set of component revisions for the complete
project. Each component keeps its own design history, documentation, and
releases.

## Components

| Component | Description |
| --- | --- |
| [`vive-charge-dock-pcba`](https://github.com/Alenux55/vive-charge-dock-pcba) | Main charging-dock PCB design. |
| [`vive-pogo`](https://github.com/Alenux55/vive-pogo) | Controller-mounted Micro-USB adapter PCB with charging contact pads. |
| [`vive-pogo-enclosure`](https://github.com/Alenux55/vive-pogo-enclosure) | Prototype printable enclosure for the controller adapter PCB. |

See each component repository for its source files, requirements, build or
export instructions, and current design status.

## Repository layout

```text
vive-charge-dock/
|-- .gitmodules
|-- README.md
|-- vive-charge-dock-pcba/   # Git submodule
|-- vive-pogo/               # Git submodule
`-- vive-pogo-enclosure/     # Git submodule
```

## Cloning the complete project

Clone the repository and initialize all submodules in one step:

```bash
git clone --recurse-submodules https://github.com/Alenux55/vive-charge-dock.git
```

If the parent repository has already been cloned without its submodules, run
this command from its root directory:

```bash
git submodule update --init --recursive
```

To update the parent and check out the component revisions it records:

```bash
git pull --recurse-submodules
git submodule update --init --recursive
```

## Making changes

Work inside a component repository as you normally would: make the change,
commit it, and push it to that component's remote repository. Then return to
this parent repository and commit the updated submodule reference:

```bash
cd vive-pogo
git add .
git commit -m "Describe the component change"
git push

cd ..
git add vive-pogo
git commit -m "Update vive-pogo submodule"
git push
```

A submodule appearing as modified in the parent usually means that the
component is checked out at a different commit or contains local changes.
Commit and push component work before updating the corresponding reference in
this repository.

## Releases

Release files and revision details live in the applicable component
repository. A commit or tag in this umbrella repository can be used to record
the exact combination of component revisions that makes up a complete dock
build.

