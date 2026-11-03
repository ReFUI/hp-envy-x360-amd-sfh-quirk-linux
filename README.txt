HP ENVY x360 Convertible 15-ds1xxx - AMD SFH DMI quirk

Patch:
  0001-amd-sfh-hp-envy-x360-15-ds1xxx.patch

What it changes:
  Adds an entry to drivers/hid/amd-sfh-hid/amd_sfh_pcie.c's dmi_sfh_table.
  The entry calls the driver's existing mp2_disable_intr() callback. That
  callback sets intr_disable = false, so interrupts remain enabled for the
  matching system.

DMI match:
  sys_vendor     HP
  product_name   HP ENVY x360 Convertible 15-ds1xxx
  board_name     87A9
  board_version  27.17

Apply to a kernel source Git tree:
  git apply --check /path/to/0001-amd-sfh-hp-envy-x360-15-ds1xxx.patch
  git apply       /path/to/0001-amd-sfh-hp-envy-x360-15-ds1xxx.patch

If git apply --check fails:
  Do not use --ignore-space-change or force the patch blindly. Inspect
  drivers/hid/amd-sfh-hid/amd_sfh_pcie.c, find dmi_sfh_table, and check whether
  the existing mp2_disable_intr callback and table still exist. Kernel source
  changes may require rebasing the hunk. If the exact DMI entry is already
  present upstream, do not apply it a second time.

This is a device-specific local workaround, not an upstream-accepted patch.
The test report describes the observed result on one machine and one kernel
build; it does not establish that every 15-ds1xxx unit has identical firmware.

Yes, this was AI generated, IDK wtf I am doing, but I do know that this is working after months of troubleshooting failed.
