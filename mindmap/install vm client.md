---
tags:
  - topic
aliases:
---
2025-01-12 10:27
# install vm client
https://www.reddit.com/r/NixOS/comments/177wcyi/best_way_to_run_a_vm_on_nixos/
poniżej config do vmów na nixos // dodatkowo instaluj qemu
```nix
{config, pkgs, ... }:

{
  programs.dconf.enable = true;
  
  users.users.gcis.extraGroups = [ "libvirtd" ];
  
  environment.systemPackages = with pkgs; [
    virt-manager
    virt-viewer
    spice 
    spice-gtk
    spice-protocol
    win-virtio
    win-spice
    gnome.adwaita-icon-theme
  ];
  
  virtualisation = {
    libvirtd = {
      enable = true;
      qemu = {
        swtpm.enable = true;
        ovmf.enable = true;
        ovmf.packages = [ pkgs.OVMFFull.fd ];
      };
    };
    spiceUSBRedirection.enable = true;
  };
  services.spice-vdagentd.enable = true;
}
```
pic dotyczy protokołu spice link też
![[Pasted image 20250106163433.png]]
https://www.spice-space.org/download.html
# References
