# УРОЧЕН ПЛАН №26
## УЧЕБНА ПРАКТИКА: КОМПЮТЪРНИ АРХИТЕКТУРИ И ОПЕРАЦИОННИ СИСТЕМИ
### XI КЛАС

---

## 1. ОСНОВНИ ДАННИ

- **Училище:** 128-мо СУ "Алберт Айнщайн", гр.София
- **Клас:** XI клас
- **Учител:** Мариян Йорданов
- **Предмет:** Учебна практика: Компютърни архитектури и операционни системи
- **Тема на урока:** Windows - интерфейс и основни настройки
- **Дата:** ____________
- **Час:** ____________
- **Продължителност:** 90 минути (2 учебни часа)
- **Тип урок:** Упражнение
- **Място на провеждане:** Компютърен кабинет

---

## 2. ЦЕЛИ И ЗАДАЧИ

### ОБРАЗОВАТЕЛНИ ЦЕЛИ:
1. Да познават структурата на Windows 11 интерфейса
2. Да могат да използват Settings и Control Panel
3. Да работят с File Explorer и системни пътища
4. Да познават PowerShell и CMD основи
5. Да конфигурират основни системни настройки

---

## 3. СЪДЪРЖАНИЕ

### ОСНОВНИ ЗНАНИЯ:
- Windows 11 десктоп и Start Menu
- File Explorer и бързи клавиши
- Системни директории: Windows, Program Files, Users
- Settings vs Control Panel
- Task Manager разширени функции
- CMD и PowerShell въведение
- Device Manager и System Information

---

## 5. ХОД НА УРОКА

### **3. НОВ МАТЕРИАЛ (40 минути)**

#### **Част 1: Windows 11 интерфейс (10 мин)**

```
ДЕСКТОП КОМПОНЕНТИ:

┌─────────────────────────────────────────────────┐
│                                                 │
│    Desktop (работен плот)                       │
│    - Shortcuts (преки пътища)                   │
│    - Files and folders                          │
│                                                 │
│                                                 │
│                                                 │
├─────────────────────────────────────────────────┤
│ 🔍 │ 📁 │ 🌐 │ ... │       [^][🔊][🔋] 10:30   │
│ Start  Task Bar Apps    System Tray   Clock    │
└─────────────────────────────────────────────────┘

Start Menu:
- Pinned apps (закачени приложения)
- Recommended (препоръчани/скорошни)
- All apps (всички приложения)
- Search (търсене)
- Power options (изключване, рестарт, сън)
```

**Клавишни комбинации:**
```
Win            - Start Menu
Win + D        - Show Desktop
Win + E        - File Explorer
Win + I        - Settings
Win + R        - Run dialog
Win + X        - Quick Link menu
Win + L        - Lock screen
Win + Tab      - Task View
Alt + Tab      - Switch windows
Ctrl + Shift + Esc - Task Manager
Win + Shift + S - Screenshot (Snipping)
```

#### **Част 2: File Explorer и системни пътища (12 мин)**

```
ВАЖНИ СИСТЕМНИ ДИРЕКТОРИИ:

C:\
├── Windows\           # Операционната система
│   ├── System32\      # 64-bit системни файлове
│   ├── SysWOW64\      # 32-bit компатибилност
│   └── Temp\          # Временни файлове
├── Program Files\     # 64-bit приложения
├── Program Files (x86)\ # 32-bit приложения
├── Users\
│   ├── Default\       # Шаблон за нови потребители
│   ├── Public\        # Споделени файлове
│   └── [Username]\    # Потребителска папка
│       ├── Desktop\
│       ├── Documents\
│       ├── Downloads\
│       ├── Pictures\
│       └── AppData\   # Приложения данни
│           ├── Local\
│           ├── LocalLow\
│           └── Roaming\
└── ProgramData\       # Споделени app данни (скрита)

СПЕЦИАЛНИ ПЪТИЩА (Shell folders):
%USERPROFILE%  = C:\Users\[Username]
%APPDATA%      = C:\Users\[Username]\AppData\Roaming
%LOCALAPPDATA% = C:\Users\[Username]\AppData\Local
%TEMP%         = C:\Users\[Username]\AppData\Local\Temp
%WINDIR%       = C:\Windows
%SYSTEMROOT%   = C:\Windows
```

**File Explorer бързи клавиши:**
```
Ctrl + N      - Нов прозорец
Ctrl + W      - Затвори прозорец
Alt + D       - Адресна лента
Ctrl + L      - Адресна лента (алтернативно)
F2            - Преименувай
F5            - Refresh
Ctrl + F      - Търсене
Ctrl + Shift + N - Нова папка
```

#### **Част 3: Settings и Control Panel (10 мин)**

```
SETTINGS (Win + I) - Модерен интерфейс:
├── System        - Display, Sound, Power, Storage
├── Bluetooth     - Bluetooth устройства
├── Network       - WiFi, Ethernet, VPN
├── Personalization - Теми, цветове, заключен екран
├── Apps          - Инсталирани приложения
├── Accounts      - Потребителски акаунти
├── Time & Language - Дата, час, език
├── Gaming        - Game Mode, captures
├── Accessibility - Достъпност
├── Privacy       - Поверителност
└── Windows Update - Актуализации

CONTROL PANEL (legacy) - Класически:
- Все още нужен за някои настройки
- Device Manager
- Administrative Tools
- Network connections advanced
- User Accounts advanced

Достъп: Win + R → control
```

#### **Част 4: CMD и PowerShell въведение (8 мин)**

```cmd
# CMD (Command Prompt) - Win + R → cmd

dir                  # Списък на файлове (като ls)
cd folder            # Смяна на директория
cd ..                # Нагоре
cls                  # Изчисти екрана
copy src dst         # Копиране
move src dst         # Преместване
del file             # Изтриване
mkdir folder         # Създай директория
rmdir folder         # Изтрий празна директория
type file.txt        # Покажи съдържание (като cat)
tree                 # Дървовидна структура

# Системна информация
systeminfo           # Детайлна информация
hostname             # Име на компютъра
ipconfig             # Мрежова конфигурация
tasklist             # Списък процеси
```

```powershell
# PowerShell - по-мощен (Win + X → Terminal)

Get-Process                    # Процеси
Get-Service                    # Услуги
Get-ChildItem (или dir, ls)    # Списък файлове
Set-Location (или cd)          # Смяна директория
Copy-Item                      # Копиране
Move-Item                      # Преместване
Remove-Item                    # Изтриване
New-Item -Type Directory       # Създай директория
Get-Content file.txt           # Покажи съдържание

# Системна информация
Get-ComputerInfo               # Информация за компютъра
Get-CimInstance Win32_BIOS     # BIOS информация
Get-Disk                       # Дискове
```

---

### **4. ПРАКТИЧЕСКА РАБОТА (30 минути)**

**Задача 1: Навигация и настройки (10 мин)**
```
1. Отворете Settings (Win + I)
2. Намерете и запишете:
   - Windows Edition: ____________
   - Version: ____________
   - Installed RAM: ____________
   - Processor: ____________
   
3. Намерете System Information (msinfo32):
   - BIOS Version: ____________
   - Total Physical Memory: ____________
```

**Задача 2: File Explorer (10 мин)**
```
1. Отворете File Explorer (Win + E)
2. Навигирайте до C:\Windows\System32
3. Намерете cmd.exe - какъв е размерът? ______
4. Отидете на %APPDATA% - какви папки има?
5. Създайте папка Test в Documents
6. Създайте текстов файл info.txt в нея
```

**Задача 3: CMD/PowerShell (10 мин)**
```
В CMD или PowerShell:
1. Покажете текущата директория
2. Покажете списък на файловете
3. Изпълнете systeminfo | findstr "OS"
4. Изпълнете ipconfig
5. Намерете IP адреса си: ____________
```

---

### **5. ОБОБЩЕНИЕ (7 минути)**

```
КЛЮЧОВИ ТОЧКИ:

1. Win + E = File Explorer, Win + I = Settings
2. %USERPROFILE% = потребителска папка
3. Settings за модерни настройки, Control Panel за advanced
4. CMD за прости команди, PowerShell за скриптове
5. Task Manager (Ctrl+Shift+Esc) за мониторинг
```

---

## 7. ПРИЛОЖЕНИЯ

### WINDOWS КОМАНДИ СПРАВОЧНИК

```cmd
# Информация
systeminfo
hostname
ver
ipconfig /all
wmic cpu get name
wmic memorychip get capacity

# Файлове
dir /a           # Всички файлове
attrib           # Атрибути
xcopy            # Разширено копиране

# Мрежа
ping google.com
tracert google.com
netstat -an
```

---

**Изготвил:** Мариян Йорданов  
**Дата на изготвяне:** Януари 2025 г.
