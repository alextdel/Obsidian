**up::** [[Linux MOC]]
**index::** [[+Index for Personal]]

**tags::** #Arch #Linux #pacman #cheatsheets 
# Pacman Command Cheat-sheet

**Created:**  17 June 2024 at  09:55 hours.
___
---

**Pacman Commands Cheatsheet**

- **Update Package Database and System:**
  ```
  sudo pacman -Syu
  ```

- **Install a Package:**
  ```
  sudo pacman -S <package_name>
  ```

- **Remove a Package:**
  ```
  sudo pacman -R <package_name>
  ```

- **Remove a Package and Unused Dependencies:**
  ```
  sudo pacman -Rns <package_name>
  ```

- **Search for a Package:**
  ```
  pacman -Ss <search_term>
  ```

- **List Installed Packages:**
  ```
  pacman -Q
  ```

- **Get Information About an Installed Package:**
  ```
  pacman -Qi <package_name>
  ```

- **Get Information About a Package in the Repos:**
  ```
  pacman -Si <package_name>
  ```

- **List Files Installed by a Package:**
  ```
  pacman -Ql <package_name>
  ```

- **Find Which Package Owns a File:**
  ```
  pacman -Qo /path/to/file
  ```

- **Remove Unused Packages (Orphans):**
  ```
  sudo pacman -Rns $(pacman -Qtdq)
  ```

- **Clean Package Cache:**
  ```
  sudo pacman -Sc
  ```

- **Clean All Cached Packages:**
  ```
  sudo pacman -Scc
  ```

- **Synchronize and Update All Packages, Forcing a Refresh of All Package Lists:**
  ```
  sudo pacman -Syyu
  ```

- **Upgrade the System and Remove Unneeded Dependencies:**
  ```
  sudo pacman -Rsn $(pacman -Qdtq)
  ```

- **Refresh the Pacman Keyring:**
  ```
  sudo pacman-key --init
  sudo pacman-key --populate archlinux
  sudo pacman-key --refresh-keys
  ```

- **Fix Mirror List and Update:**
  ```
  sudo pacman-mirrors --fasttrack
  sudo pacman -Syy
  ```

---


**See also::** 

### Links to this note:
```query
"[[Pacman Command Cheat-sheet]]"
```


