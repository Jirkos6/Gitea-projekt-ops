# Gitea projekt OPS
1. Nainstalujeme na VirtualBox SSH abychom se mohli připojit přes PuTTY, do kterého se dají příkazy vkládat
     Nainstalujeme balíček openssh-server
        - sudo apt update && sudo apt install openssh-server
     Zjistíme jestli se služba spustila
        - systemctl status ssh
     Pokud nesvítí ve výpisu zeleně "active (running)" musíme ssh zapnout
        - systemctl start ssh
     Přikázem "ip a" zjistíme ip adresu, kterou se připojíme do PuTTY ve které pokračujeme
   
2. Aktualizace systému a instalace potřebných balíčků:
     Nejprve zjistíme jestli je náš Debian aktuální:
        - sudo apt update && sudo apt upgrade -y
     Poté nainstalujeme potřebné balíčky, včetně Gitu a SSH:
        - sudo apt install git openssh-server -y

   


3. vytvoření databáze
   - sudo apt update && sudo apt upgrade -y
   - sudo apt install -y git mariadb-server nginx
   - sudo mysql_secure_installation (použijte tento příkaz separátně)
     
     sudo mysql -u root -p
     použijte tyto příkazy najednou:
     CREATE DATABASE gitea;
     GRANT ALL PRIVILEGES ON gitea.*TO 'gitea'@'localhost' IDENTIFIED BY 'test123' -|- heslo, pod kterým se přihlásíme do gitea
     FLUSH PRIVILEGES;
     EXIT;

5. vytvoření uživatele:
   - sudo adduser --system --shell /bin/bash --gecos 'Git Version Control' --group --disabled-password --home /home/git git


   
6. Stáhneme a nainstalujeme GItea:
     Provedeme pomocí příkazu wget:
           - wget -O gitea https://dl.gitea.io/gitea/1.15.6/gitea-1.15.6-linux-amd64
     Nastavíme souboru práva pro spuštění a přesunutí souboru do globálního umístění:
           - chmod +x gitea
           - sudo mv gitea /usr/local/bin/gitea
   
7. Vytvoříme uživatele a adresářouvou strukturu:
      První vytvoříme uživatele pro Gitea (s názvem "git"):
           - sudo adduser --system --shell /bin/bash --gecos 'Git Version Control' --group --disabled-password --home /home/git git
      Nastavíme potřebnou strukturu adresáře:
           - sudo mkdir -p /var/lib/gitea/{custom,data,indexers,public,log}
           - sudo chown git:git /var/lib/gitea/{data,indexers,log}
           - sudo chmod 750 /var/lib/gitea/{data,indexers,log}
           - sudo mkdir /etc/gitea
           - sudo chown root:git /etc/gitea
           - sudo chmod 770 /etc/gitea
   
8. Nastavíme systemd službu:
   Vytvoříme systemd konfigurační soubor pro Gitea:
           - sudo nano /etc/systemd/system/gitea.service
   Vložíme následující konfiguraci služby:
           [Unit]
           Description=Gitea (Git with a cup of tea)
           After=syslog.target
           After=network.target

           [Service]
           RestartSec=2s
           Type=simple
           User=git
           Group=git
           WorkingDirectory=/var/lib/gitea/
           ExecStart=/usr/local/bin/gitea web -c /etc/gitea/app.ini
           Restart=always
           Environment=USER=git HOME=/home/git GITEA_WORK_DIR=/var/lib/gitea

           [Install]
           WantedBy=multi-user.target

9.
- sudo mkdir -p /etc/gitea/custom/conf
- sudo chown -R $USER:$USER /etc/gitea
 
      
      Povolíme a spustíme Gitea:
            - sudo systemctl enable gitea
            - sudo systemctl start gitea
            - gitea

9. Přístup k Gitea webu:
        - jakmile je Gitea spuštěna, dostaneme se k němu pomocí ip adresy ("ip a") a vašeho serveru na portu 3000
                (ip_adresa:3000)
