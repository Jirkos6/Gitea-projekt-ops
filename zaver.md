# Závěr k instalaci Gitea na Debianu

## Co se povedlo:

- **Aktualizace systému a instalace potřebných balíčků:** Bez problémů.
- **Stáhnutí a nastavení Gitea:** Úspěšné.
- **Vytvoření uživatele a adresářové struktury:** Správně provedeno.
- **Nastavení systemd služby a spuštění Gitea:** Dokončeno bez chyb.

## Části, které se nepovedly:

- **Oprávnění:** Při prvním pokusu způsobily problémy s přístupem a funkcionalitou Gitea.

## Co by mohlo zaskočit:

- **Konfigurační soubor gitea** Může být komplikované pro uživatele

## Jiné varianty řešení:

- **instalace pomocí Dockeru:** Ulehčuje správu a portabilitu.
- **Automatizace procesu:** Pomocí Ansible playbooků nebo jiných nástrojů pro správu konfigurace.

## Výhody a nevýhody naší varianty:

### Výhody:

- **Flexibilita konfigurace:** Přizpůsobení specifickým potřebám.
- **Porozumění systému:** Hlubší znalosti o systému.
- **Nezávislost na externích službách:** Není závislá na cloudových službách.
- **Optimalizace zdrojů:** Možnost optimalizace využití systémových zdrojů.
- **Bezpečnost:** Přímá kontrola nad bezpečnostními aktualizacemi.

### Nevýhody:

- **Časová náročnost:** Vyžaduje více času a úsilí.
- **Složitost správy:** Bez automatizovaných nástrojů.
- **Riziko chyb:** Náchylnost k lidským chybám.
- **Technické znalosti:** Vyžaduje pokročilé znalosti Linuxu.
- **Aktualizace a závislosti:** Udržování aktuálních verzí může být náročné.

## Na co si dát pozor:

- **Oprávnění:** Provádějte kroky s příslušnými oprávněními.
- **Bezpečnostní konfigurace:** Správná konfigurace firewallu a SELinux.

## Co by bylo dobré dále prozkoumat:

- **Zálohování a obnova:** Možnosti pro Gitea.
- **Rozšiřitelnost:** Integrace s nástroji pro automatizaci vývoje.

## Jak by se mohlo pokračovat:

- **Rozšíření Gitea:** O pluginy a integrace.
- **Optimalizace:** Výkonu a zabezpečení serveru.
