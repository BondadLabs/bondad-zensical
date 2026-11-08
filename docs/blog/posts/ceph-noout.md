---
date:
  created: 2026-10-12
authors: [ehsan]
categories: [Ceph]
tags: [storage, maintenance]
---

# When to set `noout` in Ceph

Short maintenance windows are the case for `noout`: it stops Ceph from
rebalancing while an OSD host reboots.

<!-- more -->

```bash
ceph osd set noout
# reboot the host
ceph osd unset noout
```

Leave it set too long and a real failure won't trigger recovery either.
