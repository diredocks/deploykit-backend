# DeployKit backend
AOSC OS Installer (Deploykit) v2.0 backend

# Usage (test example)

Just run:

```bash
# Install dbus interface rule file:
sudo groupadd -r sysinstall
sudo usermod -a -G sysinstall USER
sudo cp ./deploykit-dbus.conf /usr/share/dbus-1/system.d

# Re-login, Build and run backend:
cargo build
sudo ./target/debug/deploykit-backend

# Run example client to install system
# First, Create a new test storage image and mount it:
sudo fallocate -l 50G ./test.img
sudo losetup -P /dev/loop30 ./test.img
sudo cfdisk /dev/loop30

# Finally, start install:
cargo run --example cli -- --user aosc --password aosc
```
