# Wymagane pluginy

Pierwszym krokiem będzie pobranie wymaganych pluginów, w tym celu pobierzemy:
1. [ajLeaderboards](https://modrinth.com/plugin/ajleaderboards/versions)
2. [PlaceholderAPI](https://hangar.papermc.io/HelpChat/PlaceholderAPI/versions)

# Podstawowa konfiguracja 

Po zainstalowaniu pluginów przechodzimy w konfiguracji [ajLeaderboards](https://modrinth.com/plugin/ajleaderboards/versions)
Konfiguracje pluginy znajdziemy pod tą ścieżką:``plugins:ajLeaderboards/config.yml``

Jak otworzyłeś konfiguracje interesuje ciebie opcja ``enable-dontupdate-permission``, ustawiasz jej wartość na **false**.

Co robi ta opcja? Wyłącza ona bypass dla administracji w topkach, jest to przydatne podczas testowania pluginu. Po skończeniu konfiguracji możesz to ponownie ustawić na **true** gdy chcesz aby administracja nie zaliczała się do topek.

# Zainstalowanie placeholderów

Kolejnym krokiem będzie instalacja placeholderów, ja chciałbym zrobić topke skoczków, dlatego pobiorę expansion: [Statistic](https://api.extendedclip.com/expansions/statistic/)

Więc do pobrania użyje komend:
- /papi ecloud download Statistic (Pamiętaj o przeładowaniu pluginu po zainstalowaniu placeholderu: /papi reload)
- /ajlb add %statistic_jump%

Listę placeholderów znajdziesz pod: [wiki.placeholderapi.com](https://wiki.placeholderapi.com/users/placeholder-list/) lub [github.com/PlaceholderAPI](https://github.com/PlaceholderAPI/PlaceholderAPI/wiki/Placeholders)

# Dodanie topek do hologramu:

**[DecentHolograms](https://modrinth.com/plugin/decentholograms):** (Zalecany gdy wpuszczasz graczy poniżej wersji 1.19.4)

- /dh create topka_skokow &b&lTOPKA SKOCZKÓW
- /dh l add topka_skokow 1 &71. &f%ajlb_lb_statistic_jump_1_alltime_name% &7- &f%ajlb_lb_statistic_jump_1_alltime_value%

Gotowy efekt: https://github.com/user-attachments/assets/03670f98-e99a-42a3-bbe2-e97faad45545

**[FancyHolograms](https://modrinth.com/plugin/fancyholograms):** (Zalecany gdy wpuszczasz graczy od wersji 1.19.4)

- /hologram create text topka_skokow
- /hologram edit topka_skokow setline 1 &b&lTOPKA SKOCZKÓW
- /hologram edit topka_skokow addline &71. &f%ajlb_lb_statistic_jump_1_alltime_name% &7- &f%ajlb_lb_statistic_jump_1_alltime_value%
- /hologram edit topka_skokow updatetextinterval 1200 (Ta opcja ustawia czas odświeżania się hologramu, wartość 1200 będzie odświeżać hologram w takim samym czasie co DecentHolograms)

Gotowy efekt: https://github.com/user-attachments/assets/daada980-6601-40e4-90bc-2f456e008429

# Dodanie topek do npc

**[Citizens](https://ci.citizensnpcs.co/job/citizens2/):** (Najmniej zalecany pod kątem optymalizacyjnym)

- /npc create top_skokow_1
- (Gdy nie masz zaznaczonego npc) /npc sel top_skokow_1 lub /npc sel i patrzysz na npc
- /npc skin %ajlb_lb_statistic_jump_1_alltime_name%

Gotowy efekt: https://github.com/user-attachments/assets/565abdbc-c0c7-4e26-8da5-fddfa65fe0e3

**[FancyNpcs](https://modrinth.com/plugin/fancynpcs):**

- /npc create top_skokow_1
- /npc skin top_skokow_1 %ajlb_lb_statistic_jump_1_alltime_name%

Gotowy efekt: https://github.com/user-attachments/assets/e9b51ee9-6c4c-45bb-a912-42a971b300cf

**[ZNPCsPLUS2](https://modrinth.com/plugin/znpcsplus):** (Zalecany) 

- Przejdź do konfiguracji tą ścieżką: ``plugins:ZNPCsPlus/config.yaml`` i przełącz opcję ``disable-skin-fetcher-warnings`` na **true**, w przeciwnym razie w konsoli będziesz otrzymywał warny (Nie wpływają one na wydajność serwera, ani na działanie pluginu)
- /npc create top_skokow player
- /npc skin top_skokow dynamic %ajlb_lb_statistic_jump_1_alltime_name% 

Gotowy efekt: https://github.com/user-attachments/assets/a30e4387-9cab-4d3b-a851-6985bf2ec499

# Dodanie topek na tabliste

**[TAB](https://modrinth.com/plugin/tab-was-taken)**

- Przejdź do konfiguracji tą ścieżką: ``plugins:TAB/config.yml`` i przejdź do opcji ``layout``, przełącz ją na **true** i ustaw w taki sposób:

```yml
layout:
  enabled: true
  direction: COLUMNS
  default-skin: mineskin:383747683
  enable-remaining-players-text: false
  remaining-players-text: '... and %s more'
  empty-slot-ping-value: 1000
  layouts:
    default:
      fixed-slots:
        - '1|&3&b&lTOPKA SKOCZKÓW:'
        - '2|&71. &f%ajlb_lb_statistic_jump_1_alltime_name% &7- &f%ajlb_lb_statistic_jump_1_alltime_value%'
        - '3|&72. &f%ajlb_lb_statistic_jump_2_alltime_name% &7- &f%ajlb_lb_statistic_jump_2_alltime_value%'
        - '4|&73. &f%ajlb_lb_statistic_jump_3_alltime_name% &7- &f%ajlb_lb_statistic_jump_3_alltime_value%'
        - '5|&74. &f%ajlb_lb_statistic_jump_4_alltime_name% &7- &f%ajlb_lb_statistic_jump_4_alltime_value%'
        - '6|&75. &f%ajlb_lb_statistic_jump_5_alltime_name% &7- &f%ajlb_lb_statistic_jump_5_alltime_value%'
        - '7|&76. &f%ajlb_lb_statistic_jump_6_alltime_name% &7- &f%ajlb_lb_statistic_jump_6_alltime_value%'
        - '8|&77. &f%ajlb_lb_statistic_jump_7_alltime_name% &7- &f%ajlb_lb_statistic_jump_7_alltime_value%'
        - '9|&78. &f%ajlb_lb_statistic_jump_8_alltime_name% &7- &f%ajlb_lb_statistic_jump_8_alltime_value%'
        - '10|&79. &f%ajlb_lb_statistic_jump_9_alltime_name% &7- &f%ajlb_lb_statistic_jump_9_alltime_value%'
        - '11|&710. &f%ajlb_lb_statistic_jump_10_alltime_name% &7- &f%ajlb_lb_statistic_jump_10_alltime_value%'
```
Gotowy efekt: https://github.com/user-attachments/assets/01352bd8-9857-4a10-8e1b-a1f435d63158

# Dodatkowe informacje

**Jak zmienić wiadomość zwrotną, gdy nie ma gracza w topce?**

- Przejdź do konfiguracji ajleaderboards: ``plugins:ajLeaderboards/config.yml`` i zmień opcje: ``no-data-name``, oraz ``no-data-score``
# Dodatkowe informacje

**Jak wyświetlać graczy online/offline w topkach?**
- /papi ecloud download Utils
- /papi ecloud download ChangeOutput
- /papi ecloud download player
- /papi reload
- Ustawiasz placeholder: ``&71. %utils_parseplaceholder:[{ajlb_lb_statistic_jump_1_alltime_name}]_changeoutput_equals_input:{player_online}_matcher:yes_ifmatch:&a{ajlb_lb_statistic_jump_1_alltime_name} &7- &a_else:&c{ajlb_lb_statistic_jump_1_alltime_name} &7- &c%%ajlb_lb_statistic_jump_1_alltime_value%``

⚠ UWAGA! Gdy placeholder jest wyświetlany, musi być już wcześniej dostepny w topce, w przeciwnym razie placeholder może spowodować obiążenie serwera.
Przykładowo: Miejsce 3 jest puste, więc do momentu gdy na miejsce 3 nie wejdzie Maciek123, placeholder będzie lagował serwer. Po zajęciu miejsca 3 i opuszczeniu przez gracza serwera problem przestanie występować. Aktualnie by to naprawić możesz w szcztuczny sposób uzupełnić topke, wchodząc przykładowo na serwer na altach.

Gotowy efekt: https://github.com/user-attachments/assets/9c72389b-cdc8-45ea-9a74-85e14dae6a7b


