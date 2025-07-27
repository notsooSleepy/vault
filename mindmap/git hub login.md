---
tags:
  - adault
aliases:
---
2025-07-26 16:32
# git hub login 
in home.nix
```nix
  home.packages = with pkgs; [
    git-credential-manager
];

  programs.git = {
    extraConfig.credential.helper = "manager";
    extraConfig.credential."https://github.com".username = "YourUserName";
    extraConfig.credential.credentialStore = "cache";
    enable = true;
  };
```

# References