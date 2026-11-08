# Admonitions

Each type takes its hue from the palette: blue, violet, green, amber, coral
or muted grey.

!!! note
    `note`, `info` and `todo` are blue. Here's a [link](index.md) and
    `inline code` inside one.

!!! abstract
    `abstract`, `summary`, `tldr` and `example` are violet.

!!! info
    Information worth knowing before you continue.

!!! tip
    `tip`, `hint`, `important`, `success`, `check` and `done` are green.

!!! success
    The operation completed.

!!! question
    `question`, `help`, `faq`, `warning`, `caution` and `attention` are amber.

!!! warning
    This will restart the node.

!!! failure
    `failure`, `fail`, `missing`, `danger`, `error` and `bug` are coral.

!!! danger
    This deletes the volume and every snapshot of it.

!!! bug
    Known issue in 0.1.0.

!!! example
    An example, with a code block:

    ```bash
    kubectl get nodes -o wide
    ```

!!! quote
    `quote` and `cite` are muted.

## Collapsible

??? note "Collapsed by default"
    Click the title to open it.

???+ warning "Open by default"
    Click the title to close it.

!!! info inline end "Inline"
    Floats beside the text.

An inline admonition sits next to this paragraph, so long lines of text wrap
around it. It's useful for side notes that shouldn't break the flow of the
page.
