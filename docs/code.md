# Code

## Python

```python title="health.py" linenums="1" hl_lines="7 8"
from dataclasses import dataclass


@dataclass
class Node:
    name: str
    gpus: int = 8  # (1)!
    ready: int = 8

    def healthy(self, threshold: float = 0.95) -> bool:
        """Return True if enough GPUs report ready."""
        return self.ready / self.gpus >= threshold
```

1.  Annotations render as a numbered marker; click it to open this note.

## Shell

```bash
# Drain a node before maintenance
kubectl drain gpu-node-07 --ignore-daemonsets --delete-emptydir-data
ceph osd set noout && echo "noout set: $(date -Iseconds)"
```

## YAML

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nvidia-smi
spec:
  restartPolicy: Never
  containers:
    - name: smi
      image: nvcr.io/nvidia/cuda:12.4.0-base-ubuntu22.04
      resources:
        limits:
          nvidia.com/gpu: 1
```

## Go

```go
package main

import "fmt"

func main() {
	for i := 0; i < 3; i++ {
		fmt.Printf("attempt %d\n", i)
	}
}
```

## Rust

```rust
fn main() {
    let nodes = vec!["a", "b", "c"];
    let count: usize = nodes.iter().filter(|n| **n != "b").count();
    println!("{count} healthy");
}
```

## Tabs

=== "pip"

    ```bash
    pip install bondad-zensical
    ```

=== "uv"

    ```bash
    uv add bondad-zensical
    ```

=== "Plain text"

    Tabs can hold any content, not only code.
