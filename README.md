# Klipper-Backup 💾 
Klipper backup script for manual or automated GitHub backups 

This backup is provided by [Klipper-Backup](https://github.com/Staubgeborener/klipper-backup).

---------------------------------------------------------------


# 1) Příprava "úložiště GitHub"
 - Přihlasit se na GitHubu
 - přejít do "Repositories"
 - vytvořit "new reposity" 
  
  !! V tuto chvíli nevytvářejte soubor README.md Později si můžete vytvořit vlastní !!


# 2) Vytvořit "GitHub token" 
 - V GitHubu klikněte na profil v pravém horním rohu
 - dále: ```Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token```
 
  Nastavení:
  - ```Token name```:**jméno tokenu**  
  - ```Only select repositories```:**jméno vytvořeného úložiště**
  
  Repository permissions:  
  - ```Contents```:**Read and write**  
  - ```Metadata```:**Read and write** or **Read-Only**
  
 - klik  ```Generate new token```
 
  ```!! zkopírovat nový token, bude potřeba později !!```
  

# 3) "INSTALACE pomocí KIAUH" 
 - vyber "E" pro Extension
 - vyber "4" pro Klipper-Backup 

 
# 4) Klipper makra pro manuální backup
```shell
[gcode_macro update_git]
gcode:
    {% set message = params.MESSAGE|default() %}
    {% if message %}
        RUN_SHELL_COMMAND CMD=update_git_script_message PARAMS="'{params.MESSAGE}'"
    {% else %}
        RUN_SHELL_COMMAND CMD=update_git_script
    {% endif %}

[gcode_shell_command update_git_script]
command: bash -c "bash $HOME/klipper-backup/script.sh"
timeout: 90.0
verbose: True

[gcode_shell_command update_git_script_message]
command: bash -c "bash $HOME/klipper-backup/script.sh -c \"$0\""
timeout: 90.0
verbose: True
```
 

# 5) zde je možno upravit přihlašovaní a další nastavení

SSH terminal
``` shell
 cd ~/klipper-backup
 ```
``` shell
 nano .env
```


