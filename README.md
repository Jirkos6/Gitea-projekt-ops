# Gitea projekt sítě
1. Aktualizace systému a instalace potřebných balíčků:
     Nejprve zjistíme jestli je náš Debian aktuální:
          sudo apt update && sudo apt upgrade -y
     Poté nainstalujeme potřebné balíčky, včetně Gitu a SSH:
           sudo apt install git openssh-server -y
   
2. Stáhneme a nainstalujeme GItea:
     Provedeme pomocí příkazu wget:
           wget -O gitea https://dl.gitea.io/gitea/1.15.6/gitea-1.15.6-linux-amd64

     
      
