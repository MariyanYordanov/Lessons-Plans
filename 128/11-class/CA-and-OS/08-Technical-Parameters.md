# УРОЧЕН ПЛАН №8
## УЧЕБНА ПРАКТИКА: КОМПЮТЪРНИ АРХИТЕКТУРИ И ОПЕРАЦИОННИ СИСТЕМИ
### XI КЛАС

---

## 1. ОСНОВНИ ДАННИ

- **Училище:** 128-мо СУ "Алберт Айнщайн", гр.София
- **Клас:** XI клас
- **Предмет:** Учебна практика: Компютърни архитектури и операционни системи
- **Тема на урока:** Технически параметри и режими на работа на микропроцесорите
- **Дата:** ____________
- **Час:** ____________
- **Продължителност:** 90 минути (2 учебни часа)
- **Тип урок:** Нови знания
- **Място на провеждане:** Компютърен кабинет

---

## 2. ЦЕЛИ И ЗАДАЧИ

### ОБРАЗОВАТЕЛНИ ЦЕЛИ:
1. Учениците да разберат основните технически параметри на процесорите
2. Да усвоят концепциите за тактова честота, IPC, TDP
3. Да познават различните режими на работа и power states
4. Да разбират технологиите за динамично управление на производителността
5. Да могат да анализират и сравняват процесорни спецификации

### ВЪЗПИТАТЕЛНИ ЦЕЛИ:
1. Формиране на разбиране за енергийна ефективност
2. Възпитаване на критично мислене при избор на хардуер
3. Развиване на интерес към процесорни технологии
4. Изграждане на техническа култура

### РАЗВИВАЩИ ЦЕЛИ:
1. Развитие на умения за анализ на технически спецификации
2. Усъвършенстване на способности за benchmark интерпретация
3. Формиране на умения за оптимизация на системи
4. Развитие на компетенции за техническа оценка

---

## 3. СЪДЪРЖАНИЕ

### ОСНОВНИ ЗНАНИЯ И УМЕНИЯ:

#### Знания:
- Архитектурни параметри: ядра, нишки, cache йерархия
- Честотни характеристики: base, boost, all-core turbo
- Термални параметри: TDP, PL1, PL2, Tjmax
- Power states: C-states, P-states, S-states
- Технологии: Turbo Boost, Precision Boost, SMT/HT
- Производствен процес и влияние върху характеристиките

#### Умения:
- Четене и разбиране на процесорни спецификации
- Мониторинг на параметри в реално време
- Конфигуриране на BIOS/UEFI настройки
- Анализ на производителност и консумация
- Избор на подходящ процесор за конкретни нужди

### ВРЪЗКИ С ДРУГИ ПРЕДМЕТИ:

1. **Физика** - полупроводници, топлообмен, електрическа мощност
2. **Математика** - експоненциални функции, статистика
3. **Химия** - силиций, производствени процеси
4. **Икономика** - price/performance анализ
5. **Екология** - енергийна ефективност, въглероден отпечатък

---

## 4. МЕТОДИ И СРЕДСТВА

### МЕТОДИ НА ПРЕПОДАВАНЕ:
1. **Интерактивна лекция** с мултимедийни материали
2. **Демонстрация** на мониторинг софтуер
3. **Практическа работа** с BIOS настройки
4. **Сравнителен анализ** на различни процесори
5. **Изследователски подход** с benchmark тестове

### УЧЕБНИ СРЕДСТВА И МАТЕРИАЛИ:
1. **Хардуер:**
   - Демонстрационни процесори (различни поколения)
   - Компютри с различни CPU
   
2. **Софтуер:**
   - CPU-Z, HWiNFO64
   - Intel XTU / AMD Ryzen Master
   - Prime95, Cinebench
   - ThrottleStop, CoreTemp
   - Task Manager, Resource Monitor
   
3. **Учебни материали:**
   - Спецификации на процесори
   - Сравнителни таблици
   - Диаграми на архитектури

---

## 5. ХОД НА УРОКА

### **1. ОРГАНИЗАЦИОНЕН МОМЕНТ (5 минути)**

**Дейност на учителя:**
- Проверка на присъствието
- Подготовка на демонстрационните системи
- Въвеждащ въпрос: "Защо един процесор 3GHz може да е по-бърз от друг 4GHz?"

**Дейност на учениците:**
- Подготовка за урока
- Споделяне на предположения

### **2. АКТУАЛИЗАЦИЯ НА ЗНАНИЯТА (8 минути)**

**Дейност на учителя:**
- Преговор на основни концепции

**Въпроси за преговор:**
1. Какво е CPU и каква е функцията му?
2. Какво означава тактова честота?
3. Какво е многоядрен процесор?
4. Защо процесорите се нагряват?

**Кратка демонстрация:**
- Отваряне на Task Manager
- Показване на CPU използване и честота
- Наблюдение на промените при натоварване

### **3. НОВ МАТЕРИАЛ (45 минути)**

#### **Част 1: Основни технически параметри (15 мин)**

**Архитектурни характеристики:**

```
Процесорна архитектура - пример Intel Core i7-13700K:

Cores & Threads:
- 8 Performance cores (P-cores)
- 8 Efficiency cores (E-cores)
- 24 threads total (HT on P-cores)

Cache йерархия:
- L1: 80KB per P-core, 96KB per E-core
- L2: 2MB per P-core, 4MB per E-core cluster
- L3: 30MB shared (Smart Cache)

Честоти:
- P-cores: 3.4 GHz base, 5.4 GHz turbo
- E-cores: 2.5 GHz base, 4.2 GHz turbo
- All-core turbo: ~5.1 GHz (P), ~3.9 GHz (E)
```

**Ключови параметри:**

**1. IPC (Instructions Per Clock):**
```
Производителност = IPC × Frequency × Cores

Пример:
CPU A: 4 GHz, IPC=1.0 → 4 единици
CPU B: 3 GHz, IPC=1.5 → 4.5 единици
CPU B е по-бърз въпреки по-ниската честота!
```

**2. Производствен процес:**
```
Еволюция на технологичните възли:
14nm → 10nm → 7nm → 5nm → 3nm

Предимства на по-малък процес:
✓ По-ниска консумация
✓ По-висока плътност (повече транзистори)
✓ По-високи честоти
✓ По-малко топлина

Сравнение:
Intel 10nm ≈ TSMC 7nm (маркетинг разлики)
```

**3. TDP и термални лимити:**
```
TDP (Thermal Design Power):
- Номинална топлинна мощност
- НЕ е максимална консумация!

Intel Power Limits:
- PL1 (TDP): Дългосрочен лимит (125W)
- PL2: Краткосрочен burst (253W)
- Tau: Време на PL2 (56s)

AMD:
- PPT: Package Power Tracking (142W)
- TDC: Thermal Design Current (95A)
- EDC: Electrical Design Current (140A)

Tjmax (Junction Temperature):
- Intel: 100°C
- AMD: 90-95°C
```

#### **Част 2: Режими на работа и Power States (12 мин)**

**C-States (CPU Idle States):**
```
C0: Active - CPU изпълнява инструкции
C1: Halt - Clock stopped, быстро събуждане
C1E: Enhanced Halt - Намалено напрежение
C3: Deep Sleep - L1/L2 cache flush
C6: Deep Power Down - Core напрежение ~0V
C7: Deeper Sleep - LLC може да се изчисти
C8-C10: Package states - Uncore sleep

Латентност на събуждане:
C1: <1μs
C3: ~50μs
C6: ~100μs
C10: ~200μs
```

**P-States (Performance States):**
```
P0: Maximum performance (Turbo)
P1: Nominal frequency (Base)
P2-Pn: Намалени честоти
Pn: Minimum frequency

SpeedStep (Intel) / Cool'n'Quiet (AMD):
- Динамично регулиране на V/F
- Voltage-Frequency curve
- Енергийна ефективност

Пример преходи:
Idle: 800MHz @ 0.8V (5W)
Load: 4500MHz @ 1.35V (125W)
```

**S-States (System Sleep States):**
```
S0: Working
S1: Standby (CPU stopped, RAM active)
S2: Deeper standby (CPU off, RAM active)
S3: Suspend to RAM (STR)
S4: Hibernate (Suspend to disk)
S5: Soft off
```

**Turbo/Boost технологии:**
```
Intel Turbo Boost 3.0:
- Идентифицира най-бързите 2 ядра
- Favored cores до +200MHz
- Thread Director за hybrid архитектури

AMD Precision Boost 2:
- Opportunistic boosting
- XFR (Extended Frequency Range)
- PBO (Precision Boost Overdrive)

Фактори влияещи на boost:
1. Температура
2. Power limits
3. Брой активни ядра
4. Тип натоварване
```

#### **Част 3: Мониторинг и анализ (10 мин)**

**Софтуерни инструменти:**

**CPU-Z информация:**
```
Tabs и какво показват:
- CPU: Model, Specification, Clocks
- Caches: L1/L2/L3 sizes and latency
- Mainboard: Chipset, BIOS
- Memory: Speed, timings
- SPD: Memory modules info
- Bench: Quick benchmark
```

**HWiNFO64 сензори:**
```
Важни метрики:
- Core Clocks (Current/Min/Max/Avg)
- Core Temps (Tdie, Tctl, Tjunction)
- Package Power (W)
- Core Voltages (VID, Vcore)
- Utilization (%)
- Thermal Throttling (Yes/No)
- Power Limit Throttling
```

**Демонстрация в реално време:**
1. Стартиране на HWiNFO64
2. Отваряне на сензори
3. Пускане на stress test (Prime95)
4. Наблюдение на:
   - Честотите се вдигат до boost
   - Температурите растат
   - Power consumption скача
   - Eventual throttling

#### **Част 4: Сравнителен анализ (8 мин)**

**Процесорни класове и сегменти:**

```
Desktop сегменти:
Entry: i3/Ryzen 3 (4-6 cores)
Mainstream: i5/Ryzen 5 (6-12 cores)
Performance: i7/Ryzen 7 (8-16 cores)
HEDT: i9/Ryzen 9 (12-24 cores)
Extreme: Threadripper/Xeon W (32-64 cores)

Mobile сегменти:
U-series: 15-28W (Ultrabooks)
P-series: 28-45W (Thin performance)
H-series: 45-55W (Gaming/Workstation)
HX-series: 55W+ (Desktop replacement)
```

**Benchmark метрики:**
```
Single-threaded:
- Важно за: Gaming, общо използване
- Тестове: Cinebench R23 ST, CPU-Z bench

Multi-threaded:
- Важно за: Rendering, компилация
- Тестове: Cinebench R23 MT, Blender

Специализирани:
- AVX-512: Scientific computing
- Quick Sync: Video encoding
- AI acceleration: NPU/AMX
```

### **4. ЗАТВЪРЖДАВАНЕ (27 минути)**

#### **Практическа работа: Анализ и оптимизация**

**Задача 1: Спецификации и мониторинг (10 мин)**

**Изследване на локалната система:**
```
1. Отворете CPU-Z
   - Запишете: Model, Cores, Threads, Cache
   - Проверете Specification string
   - Вижте Instructions sets

2. Стартирайте HWiNFO64
   - Намерете CPU раздела
   - Запишете Base/Boost clocks
   - Проверете TDP/Power Limits

3. Task Manager Performance
   - Наблюдавайте utilization
   - Проверете Speed variations
   - Вижте Up time
```

**Таблица за попълване:**
| Параметър | Стойност | Нормална ли е? |
|-----------|----------|----------------|
| CPU Model | | |
| Cores/Threads | | |
| Base Clock | | |
| Current Clock | | |
| Temperature | | |
| Utilization | | |

**Задача 2: Stress тестване (10 мин)**

**Prime95 конфигурации:**
```
Small FFTs:
- Максимален heat output
- Тества стабилност и cooling
- Наблюдавайте temps и throttling

Large FFTs:
- Тества RAM и cache
- По-реалистично натоварване

Blend:
- Комбиниран тест
- Най-близък до реални условия
```

**Протокол на тестване:**
```
1. Idle measurements (1 min):
   - Frequency: _____MHz
   - Temperature: _____°C
   - Power: _____W

2. Run Small FFTs (3 min):
   - Max Frequency: _____MHz
   - Max Temperature: _____°C
   - Max Power: _____W
   - Throttling? Yes/No

3. Cool down (2 min)

4. Run Blend test (3 min):
   - Avg Frequency: _____MHz
   - Avg Temperature: _____°C
   - Stable? Yes/No
```

**Задача 3: BIOS/UEFI настройки (7 мин)**

**Навигация в BIOS (демонстрация):**
```
Advanced CPU Configuration:
- Intel SpeedStep: Enable/Disable
- Turbo Boost: Enable/Disable
- C-States: Auto/Disable/Enable
- Power Limits: PL1/PL2 values
- AVX Offset: 0-5 (намалява честота при AVX)

Важни настройки:
- CPU Ratio: Auto/Manual
- CPU Voltage: Auto/Offset/Manual
- Load Line Calibration
- Current limits
```

**Сценарии за конфигурация:**

A. **Maximum Performance:**
```
- Disable C-States
- Maximize Power Limits
- Disable thermal throttling
- Fixed high frequency
Резултат: Висока производителност, висока консумация
```

B. **Power Saving:**
```
- Enable all C-States
- Enable SpeedStep
- Lower Power Limits
- Balanced power plan
Резултат: Ниска консумация, динамична производителност
```

C. **Quiet Operation:**
```
- Lower TDP limits
- Custom fan curves
- Enable C-States
- Slight undervolt
Резултат: Тиха работа, умерена производителност
```

### **5. ОБОБЩЕНИЕ (10 минути)**

**Ключови концепции:**
- Честотата не е единственият фактор за производителност
- IPC и архитектура са критични
- Power limits определят sustained performance
- Cooling е важен за поддържане на boost

**Сравнителен анализ:**
```
Избор на процесор според нужди:

Gaming:
- Приоритет: Single-thread performance
- Препоръка: i5-13600K, Ryzen 7 7700X

Content Creation:
- Приоритет: Multi-thread performance
- Препоръка: i9-13900K, Ryzen 9 7950X

Office/General:
- Приоритет: Efficiency, value
- Препоръка: i5-13400, Ryzen 5 7600

Server/Workstation:
- Приоритет: Cores, ECC support
- Препоръка: Xeon, Threadripper PRO
```

**Въпроси за дискусия:**
1. Защо Apple M-series са толкова ефективни?
2. Какво е бъдещето - повече ядра или по-бързи ядра?
3. Как big.LITTLE променя играта?

### **6. ДОМАШНА РАБОТА (5 минути)**

**Задачи:**

1. **Сравнителен анализ:**
   - Изберете 3 процесора в ценови диапазон 400-500 лв
   - Сравнете: cores, frequency, TDP, benchmarks
   - Препоръчайте за различни use cases
   - Таблица + 1 страница анализ

2. **Изследователска задача:**
   - Проучете Intel Thread Director технологията
   - Как работи с Windows 11 scheduler?
   - Сравнете с AMD Chiplet дизайн

3. **Практическа задача:**
   - Мониторирайте домашния CPU за 24 часа
   - Запишете: temps, frequencies, power
   - Идентифицирайте patterns на използване
   - Графики и анализ

**Срок:** До следващия учебен час

---

## 6. ОЦЕНЯВАНЕ

### КРИТЕРИИ ЗА ОЦЕНЯВАНЕ:

| Критерий | Точки |
|----------|-------|
| Познаване на параметри | 25% |
| Работа с мониторинг софтуер | 20% |
| Анализ на резултати | 20% |
| Разбиране на power states | 15% |
| Сравнителен анализ | 15% |
| Активност | 5% |

### ОЦЕНЪЧНА РУБРИКА:
- **Отличен (6):** Детайлно разбира всички параметри, прави точен анализ, предлага оптимизации
- **Много добър (5):** Познава основните концепции, анализира с малки грешки
- **Добър (4):** Базово разбиране, нуждае се от насочване при анализ
- **Среден (3):** Минимални познания, затруднения с практическата част

---

## 7. РЕФЛЕКСИЯ И АНАЛИЗ

### ВЪПРОСИ ЗА САМООЦЕНКА:
1. Разбирам ли разликата между TDP и реална консумация?
2. Мога ли да обясня защо CPU throttle-ва?
3. Знам ли как да оптимизирам за различни нужди?
4. Умея ли да чета и сравнявам спецификации?

### ИНДИКАТОРИ ЗА УСПЕХ:
- [ ] 90% разбират концепцията за IPC
- [ ] 85% могат да използват мониторинг софтуер
- [ ] 80% разбират power states
- [ ] 75% могат да анализират benchmark резултати

---

## 8. ПРИЛОЖЕНИЯ

### ПРИЛОЖЕНИЕ 1: ПРОЦЕСОРНИ СПЕЦИФИКАЦИИ 2025

**Intel 14th Gen (Raptor Lake Refresh):**
```
i9-14900K: 8P+16E, 24C/32T, 6.0GHz, 253W
i7-14700K: 8P+12E, 20C/28T, 5.6GHz, 253W
i5-14600K: 6P+8E, 14C/20T, 5.3GHz, 181W
i5-14400: 6P+4E, 10C/16T, 4.7GHz, 148W

AMD Ryzen 7000 (Zen 4):
7950X: 16C/32T, 5.7GHz, 170W
7900X: 12C/24T, 5.6GHz, 170W
7700X: 8C/16T, 5.4GHz, 105W
7600X: 6C/12T, 5.3GHz, 105W
```

### ПРИЛОЖЕНИЕ 2: МОНИТОРИНГ КОМАНДИ

**Windows PowerShell:**
```powershell
# CPU информация
Get-WmiObject Win32_Processor | Select-Object Name, NumberOfCores, MaxClockSpeed

# Температури (ако поддържа WMI)
Get-WmiObject MSAcpi_ThermalZoneTemperature -Namespace "root/wmi"

# Power план
powercfg /list
powercfg /query
```

**Linux команди:**
```bash
# CPU info
lscpu
cat /proc/cpuinfo

# Frequencies
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq

# Temperatures
sensors

# Power states
cpupower frequency-info
turbostat
```

### ПРИЛОЖЕНИЕ 3: ФОРМУЛИ И ИЗЧИСЛЕНИЯ

**Power и Performance:**
```
Dynamic Power = C × V² × f
където:
C = Capacitance
V = Voltage
f = Frequency

Performance per Watt = Performance / Power

Amdahl's Law:
Speedup = 1 / ((1-P) + P/N)
където:
P = Parallel portion
N = Number of processors

Thermal calculations:
ΔT = P × θ
където:
ΔT = Temperature rise
P = Power (W)
θ = Thermal resistance (°C/W)
```

---

**Изготвил:** [Име на учителя]  
**Дата на изготвяне:** Декември 2024 г.
