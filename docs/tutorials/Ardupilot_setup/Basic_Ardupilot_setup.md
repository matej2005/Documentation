# Návod na nastavení a kalibraci řídicí jednotky (ArduPilot)

## 1. Základní nastavení a kalibrace

- **Zvolení typu rámu**
- **Nastavení orientace AHRS:**
  - Parametr: `AHRS_ORIENTATION`
- **Kalibrace akcelerometru:**
  - Tlačítko/možnost **Calibrate Accel** (první políčko)
- **Nastavení portu pro RC přijímač:**
  - Na příslušný UART nastavte `Mavlink2` a přenosovou rychlost `460800` v záložce *Serial Ports* nebo ve *Full Parameter List*.
- **Nastavení RSSI:**
  - `RSSI_TYPE = 5` (*TelemetryRadioRSSI*)
- **Kontrola rádia:**
  - V záložce *Radio Calibration* zkontrolujte, zda jsou všechny kanály správně namapovány, případně je upravte přímo ve vysílači.
- **Nastavení přepínače letových režimů (Flight Modes):**
  - Nastavte parametr `FLTMODE_CH` na požadovaný RC kanál.
  - V záložce *Flight Modes* zvolte požadované letové režimy.
- **Nastavení Pomocných spínačů (`RCx_OPTION`):**
  - `ArmDisarm` (pro verze 4.2 a vyšší)
  - `Motor Emergency Stop`
- **Nastavení výstupů serv (Servo Output):**
  - Přiřaďte motory na požadované výstupy (nejčastěji motory 1–4 na porty 1–4).
- **Nastavení ESC / DSHOT:**
  - Nastavte pomocí parametrů:
    - `SERVO_BLH_BDMASK`
    - `SERVO_BLH_MASK`
    - `SERVO_BLH_OTYPE`
    - `SERVO_DSHOT_ESC`
    - `SERVO_BLH_AUTO` (pro pass-thru)
    - `MOT_PWM_TYPE`
- **Test a směr motorů:**
  - Pomocí funkce **Motor Test** ověřte správné pořadí motorů v *Servo Output*.
  - Následně ověřte a nastavte jejich směr otáčení pomocí parametru `SERVO_BLH_RVMASK`.
- **Failsafe:**
  - Nastavte všechny Failsafe funkce na možnost **Land** (přistání) pro bezpečnost prvního testovacího letu.
- **Kalkulace parametrů:**
  - Proveďte **Initial Tune Parameter calculation** a uložte hodnoty do řídicí jednotky (**Write to FC**).
- **Kalibrace kompasu:**
  - Zkalibrujte kompas (doporučujeme provádět venku mimo rušivé vlivy).

---

## 2. Quick Tune (Rychlé ladění PID)

1. Otevřete záložku **MAVFtp**.
2. Ve složce `APM` vytvořte složku `scripts`.
3. Do vzniklé složky nahrajte skript `VTOL quicktune.lua`.
4. Povolte skriptování nastavením parametru `SCR_ENABLE = 1`.
5. Zapněte QuickTune skript nastavením parametru `QUIK_ENABLE = 1`.
6. Nastavte funkci `Scripting1` na požadovaný spínač pomocí příslušného `RCx_OPTION`.
7. **Postup při ladění:**
   - Po vzletu přepněte spínač do **prostřední polohy** (spustí se ladění).
   - Jakmile se zobrazí hlášení *tuning done*, uložte naměřené hodnoty posunutím spínače do **spodní polohy**.
   - Po disarmování dronu vraťte spínač do **horní polohy**.

*Tímto je základní PID tune hotový.*