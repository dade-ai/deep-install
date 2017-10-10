bazel
===

releases
---
- check new release. https://github.com/bazelbuild/bazel/releases

0.5.4
---

```
wget  https://github.com/bazelbuild/bazel/releases/download/0.5.4/bazel-0.5.4-installer-linux-x86_64.sh

chmod +x bazel-0.5.4-installer-linux-x86_64.sh
sudo ./bazel-0.5.4-installer-linux-x86_64.sh
bazel
sudo cp /usr/local/lib/bazel/bin/bazel-complete.bash /etc/bash_completion.d/bazel-complete.sh
source /etc/bash_completion.d/bazel-complete.sh
```
