# Screensaver
Screensaver dohledu Zabbix

Popis:
Cílem bylo vytvořit screensaver, který se automaticky spustí po startu počítače a přihlásí na Zabbix bez nutnosti jakékoli interakce. 
Screensaver je schopen zobrazit i několik různých stránek po sobě, ale automatické přihlášení funguje pouze pro Zabbix.

Zavedení screensaveru:
- Před samotnou instalací je třeba nastavit oprvánění “full Control“ pro skupinu „Authenticated Users“ na registr „HKU:\.DEFAULT\Control Panel\Desktop“ 
  - důvod proč ./DEFAULT: po startu pc se jako první přihlašuje ./Default (účet systému), 
  - důvod proč práva: jinak nebudete schoptni zapsat parametry do registru při konfiguraci screensaveru
- screensaver primárně ukládám do system32 mezi ostatní screensavery windows, ale lze ho uložit kamkoli na systémový disk
- spusťte kontextové okno screensaveru -> install 

Nastavení:
- Screensaver funguje v několika režimech:
  1) Zobrazí stránku, která je první v seznamu stránek s možnosti přerušení screensaveru pohybem myši
  2) Přepíná zavedené stránky v definovaném časovém intervalu
  - v případě nevybrání žádné z možností screensaver zobrazí pouze první stránku v seznamu, která se nebude vypínát pohybem myši
  - důvod proč lze vybrat jen jednu z možností: funkce vypnutí pohybem myši a přepínání mezi vícero stránkami funguje pouze pod uživatelským účtem. V případě systému dochází v momentě přehození stránky k přerušení screensaveru (chyba nebyla nalezena). Rovněž bylo zjištěno, že v případě více stránek uživatel někdy nestačí zachytit zobrazované informace, proto jsou v tomto případě přidána tlačítka pro vynucené přepnutí nebo pozastavení stránek a tak vypnutí pohybem není žádoucí
- smazání nebo posunutí adresy stránky v seznamu provedete prostřednictvím pravého tlačítka myši na vybrané adrese

Poznámka k nastavení:
  - nezapomenout na vypínání displeje v nastavení windows
  - nainportovat certifikáty (jestli jsou potřeba), aby bylo možné se na stránku dostat 
  - do nastavení screensaveru se nelze dostat v případě zaplého applockeru 
 
Po nastavení jsou v registru „HKU:\.DEFAULT\Control Panel\Desktop“ nastaveny hodnoty:
   - ScreenSaveActive : 1 --spuštění screensaveru
   - ScreenSaveTimeOut : 30 --nastavení času spuštění screensaveru po neaktivitě (v sekundách)
   - SCRNSAVE.EXE : cesta ke screensaveru
Vytvoření „HKU:\.DEFAULT\Control Panel\Desktop\screensaver“   
   - CloseOnActivity : True/False --přerušit pohybem myši
   - RandomOrder : True/False --přepínání stránek
   - RotationInterval : čas přepínání stránek (v sekundách)
   - SCRLOG a SCRPASS: přihlašovací jmeno a heslo v zašifrovaném tvaru
   - Url : řetězec s url, adresy jsou odděleny mezerou a adresa na začátku je první v pořadí seznamu
   
Prostor pro zlepšení
 - vyřešit přihlašovací formulář pro různé druhy stránek
 - možnost se příhlásit pod různými hesly na více stránek
   
  
    
    
 
 
