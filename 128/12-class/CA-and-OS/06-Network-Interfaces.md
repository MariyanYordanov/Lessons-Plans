# УРОЧЕН ПЛАН №6
## УЧЕБНА ПРАКТИКА: КОМПЮТЪРНИ АРХИТЕКТУРИ И ОПЕРАЦИОННИ СИСТЕМИ
### XII КЛАС

---

## 1. ОСНОВНИ ДАННИ

- **Училище:** ПГИ „Професор д-р Асен Златаров"
- **Клас:** XII клас
- **Предмет:** Учебна практика: Компютърни архитектури и операционни системи
- **Тема на урока:** Мрежови интерфейси - 10G Ethernet, Wi-Fi 6
- **Дата:** ____________
- **Час:** ____________
- **Продължителност:** 90 минути (2 учебни часа)
- **Тип урок:** Нови знания
- **Място на провеждане:** Компютърна лаборатория

---

## 2. ЦЕЛИ И ЗАДАЧИ

### ОБРАЗОВАТЕЛНИ ЦЕЛИ:
1. Учениците да разберат еволюцията на мрежовите технологии
2. Да усвоят спецификациите на 10 Gigabit Ethernet
3. Да познават стандартите Wi-Fi 6/6E/7
4. Да разбират физическите и протоколни слоеве
5. Да могат да избират подходящи мрежови решения

### ВЪЗПИТАТЕЛНИ ЦЕЛИ:
1. Формиране на разбиране за мрежова инфраструктура
2. Възпитаване на системен подход при планиране
3. Развиване на интерес към мрежови технологии
4. Изграждане на професионални компетенции

### РАЗВИВАЩИ ЦЕЛИ:
1. Развитие на умения за анализ на мрежови нужди
2. Усъвършенстване на способности за troubleshooting
3. Формиране на умения за оптимизация на мрежи
4. Развитие на компетенции за проектиране

---

## 3. СЪДЪРЖАНИЕ

### ОСНОВНИ ЗНАНИЯ И УМЕНИЯ:

#### Знания:
- Ethernet еволюция: 10/100/1000/2.5G/5G/10G/25G/40G/100G
- 10GBASE стандарти: SR, LR, T, кабели и конектори
- Wi-Fi поколения: 802.11n/ac/ax/be
- MIMO, MU-MIMO, OFDMA технологии
- Мрежови протоколи и QoS
- Сигурност: WPA3, 802.1X

#### Умения:
- Конфигуриране на 10G мрежови карти
- Терминиране на оптични и мед кабели
- Настройка на Wi-Fi 6 access points
- Мрежова диагностика и тестване
- Оптимизация на производителност
- Планиране на мрежова инфраструктура

### ВРЪЗКИ С ДРУГИ ПРЕДМЕТИ:

1. **Мрежи и комуникации** - OSI модел, протоколи
2. **Физика** - електромагнитни вълни, оптика
3. **Математика** - модулации, Fourier transform
4. **Информационна сигурност** - криптиране, протоколи
5. **Бази данни** - мрежови изисквания за DB системи

---

## 4. МЕТОДИ И СРЕДСТВА

### МЕТОДИ НА ПРЕПОДАВАНЕ:
1. **Интерактивна презентация** с демонстрации
2. **Практическа работа** с мрежово оборудване
3. **Лабораторни измервания** на скорост и латентност
4. **Сравнителен анализ** на технологии
5. **Case studies** на реални мрежи

### УЧЕБНИ СРЕДСТВА И МАТЕРИАЛИ:
1. **Хардуер:**
   - 10G мрежови карти и switch
   - Wi-Fi 6/6E рутери и AP
   - Различни типове кабели (Cat6a, Cat7, fiber)
   - Тестово оборудване
   
2. **Софтуер:**
   - iPerf3 за bandwidth тестове
   - Wireshark за packet analysis
   - WiFi Analyzer
   - Network monitoring tools
   
3. **Учебни материали:**
   - Схеми на мрежови топологии
   - Таблици със стандарти
   - Спецификации на оборудване

---

## 5. ХОД НА УРОКА

### **1. ОРГАНИЗАЦИОНЕН МОМЕНТ (5 минути)**

**Дейност на учителя:**
- Проверка на присъствието
- Подготовка на демонстрационното оборудване
- Въвеждащ въпрос: "Защо домашният интернет е бавен въпреки 1Gbps връзка?"

**Дейност на учениците:**
- Подготовка за урока
- Споделяне на опит с мрежови проблеми

### **2. АКТУАЛИЗАЦИЯ НА ЗНАНИЯТА (8 минути)**

**Дейност на учителя:**
- Преговор на основни мрежови концепции

**Въпроси за преговор:**
1. Какво е bandwidth vs throughput?
2. Какви са слоевете на OSI модела?
3. Разлика между hub, switch и router?
4. Какво е латентност и jitter?

**Кратка демонстрация:**
- Speed test на различни връзки
- Показване на network utilization
- ping и traceroute примери

### **3. НОВ МАТЕРИАЛ (47 минути)**

#### **Част 1: 10 Gigabit Ethernet (15 мин)**

**Еволюция на Ethernet:**
```
Timeline на скоростите:
1973: 3 Mbps (Original Ethernet)
1985: 10 Mbps (10BASE-T)
1995: 100 Mbps (Fast Ethernet)
1999: 1 Gbps (Gigabit Ethernet)
2002: 10 Gbps (10 Gigabit Ethernet)
2010: 40/100 Gbps
2017: 200/400 Gbps
2025: 800 Gbps/1.6 Tbps (в разработка)

Междинни скорости (NBASE-T):
2.5GBASE-T: За Wi-Fi 6 APs
5GBASE-T: Баланс скорост/разход
```

**10GBASE стандарти:**

```
Медни кабели (10GBASE-T):
- Кабел: Cat6a (55m), Cat7 (100m)
- Конектор: RJ-45
- Power: 6-10W per port
- Латентност: 2-2.5μs
- Предимства: Съвместимост, лесен монтаж
- Недостатъци: Power consumption, heat

Оптични стандарти:
10GBASE-SR (Short Range):
- Multi-mode fiber (MMF)
- До 300m (OM3), 400m (OM4)
- 850nm wavelength
- SFP+ модули

10GBASE-LR (Long Range):
- Single-mode fiber (SMF)
- До 10km
- 1310nm wavelength
- По-скъпи модули

DAC кабели (Direct Attach Copper):
- SFP+ to SFP+
- До 7-10m
- Най-евтино решение
- За within-rack връзки
```

**Network Interface Cards (NIC):**
```
Чипсети и производители:
- Intel X550/X710/E810
- Mellanox/NVIDIA ConnectX
- Broadcom BCM57xxx
- Aquantia/Marvell AQtion

Функции:
- RSS (Receive Side Scaling)
- SR-IOV виртуализация
- RDMA support
- Hardware offload (TSO, LRO)
- Jumbo frames (9000 bytes)

PCIe изисквания:
- PCIe 3.0 x4 минимум
- PCIe 3.0 x8 за dual-port
- PCIe 4.0 x4 за future-proof
```

#### **Част 2: Wi-Fi 6 (802.11ax) и следващи поколения (15 мин)**

**Wi-Fi еволюция:**
```
Generation  | Standard  | Max Speed | Frequency | Year
------------|-----------|-----------|-----------|------
Wi-Fi 4     | 802.11n   | 600 Mbps  | 2.4/5 GHz | 2009
Wi-Fi 5     | 802.11ac  | 6.9 Gbps  | 5 GHz     | 2014
Wi-Fi 6     | 802.11ax  | 9.6 Gbps  | 2.4/5 GHz | 2019
Wi-Fi 6E    | 802.11ax  | 9.6 Gbps  | 6 GHz     | 2020
Wi-Fi 7     | 802.11be  | 46 Gbps   | 2.4/5/6   | 2024
```

**Wi-Fi 6 ключови технологии:**

**1. OFDMA (Orthogonal Frequency Division Multiple Access):**
```
Wi-Fi 5: OFDM - цял канал за един user
Wi-Fi 6: OFDMA - канал разделен на RUs

Resource Units (RUs):
- 26 тона (2 MHz) - IoT устройства
- 52 тона (4 MHz) - Voice/малък data
- 106 тона (8 MHz) - Среден traffic
- 242 тона (20 MHz) - Video streaming
- 484 тона (40 MHz) - Large transfers
- 996 тона (80 MHz) - Maximum throughput

Предимства:
✓ По-ниска латентност
✓ По-добра ефективност
✓ Повече едновременни устройства
```

**2. MU-MIMO (Multi-User MIMO):**
```
Wi-Fi 5: DL MU-MIMO 4×4
Wi-Fi 6: DL/UL MU-MIMO 8×8

Spatial streams:
1×1: Phones, IoT (433 Mbps)
2×2: Laptops (1.2 Gbps)
3×3: Premium laptops (1.8 Gbps)
4×4: Desktops, APs (2.4 Gbps)
8×8: High-end APs (4.8 Gbps)

Beamforming:
- Explicit beamforming
- Sounding procedure
- Per-user optimization
```

**3. 1024-QAM модулация:**
```
Модулация еволюция:
Wi-Fi 4: 64-QAM (6 bits/symbol)
Wi-Fi 5: 256-QAM (8 bits/symbol)
Wi-Fi 6: 1024-QAM (10 bits/symbol)

25% повече данни за символ
Изисква high SNR (>35 dB)
Работи на близко разстояние
```

**4. Target Wake Time (TWT):**
```
Negotiated sleep/wake schedule
За IoT и battery устройства
До 4× battery life improvement

Параметри:
- Wake interval
- Wake duration
- Start time offset
```

**Wi-Fi 6E допълнения:**
```
6 GHz spectrum (5.925-7.125 GHz):
- 1200 MHz нов спектър
- 14 допълнителни 80 MHz канала
- 7 допълнителни 160 MHz канала
- Без legacy устройства
- По-малко interference

Ограничения:
- По-къс обхват (higher frequency)
- Не преминава през стени добре
- Нужни нови устройства
```

#### **Част 3: Практически съображения (10 мин)**

**Кабелна инфраструктура:**
```
За 10GBASE-T:
Cat6a спецификации:
- 500 MHz bandwidth
- Individual pair shielding
- Alien crosstalk mitigation
- 23 AWG conductors typical
- Bend radius: 4× cable diameter

Fiber optic за 10G:
OM3: 50/125μm, aqua color
OM4: 50/125μm, aqua/violet
OM5: 50/125μm, lime green
OS2: 9/125μm single-mode, yellow

Конектори:
- LC: Най-популярен за 10G
- SC: Legacy
- MPO/MTP: За 40/100G
```

**Switch конфигурация:**
```
VLAN setup за 10G:
- Jumbo frames enable (9000 MTU)
- Flow control настройки
- Buffer tuning
- Storm control limits

Link aggregation (LAG):
- LACP (802.3ad)
- Static LAG
- Load balancing методи:
  - src-dst-ip
  - src-dst-mac
  - src-dst-port
```

**Wi-Fi планиране:**
```
Coverage planning:
- -67 dBm за data
- -75 dBm за basic connectivity
- 20% overlap между APs

Channel planning:
2.4 GHz: 1, 6, 11 (non-overlapping)
5 GHz: 36, 40, 44, 48... (20+ channels)
6 GHz: Preferred Scanning Channels (PSC)

Capacity planning:
- 25-30 устройства per AP (enterprise)
- 50-75 устройства (high-density)
- Airtime fairness enabled
```

#### **Част 4: Performance и troubleshooting (7 мин)**

**Benchmark тестове:**
```bash
# iPerf3 за 10G тестване
# Server:
iperf3 -s

# Client:
iperf3 -c 192.168.1.100 -t 30 -P 4

# Очаквани резултати:
# 10GBASE-T: 9.4-9.5 Gbps
# Wi-Fi 6 (160MHz): 1.8-2.2 Gbps
# Wi-Fi 6E: 2.4 Gbps

# Latency test:
ping -c 1000 192.168.1.1
# 10G: <0.1ms local
# Wi-Fi 6: 1-3ms typical
```

**Troubleshooting tools:**
```
Layer 1 (Physical):
- Cable tester/certifier
- Optical power meter
- OTDR за fiber
- Spectrum analyzer за Wi-Fi

Layer 2 (Data Link):
- Wireshark capture
- Switch port statistics
- MAC address tables
- STP status

Layer 3+ (Network+):
- traceroute/mtr
- netstat connections
- ss socket statistics
- tcpdump analysis
```

### **4. ЗАТВЪРЖДАВАНЕ (25 минути)**

#### **Практическа работа: Конфигуриране и тестване**

**Задача 1: 10G мрежа setup (10 мин)**

```
Конфигурация на NIC:
1. Инсталиране на драйвери
2. Настройка на IP адрес
3. Enable jumbo frames:
   Windows: Device Manager → Advanced
   Linux: ip link set dev eth0 mtu 9000
   
4. Performance tuning:
   - RSS queues
   - Interrupt moderation
   - Receive buffers

5. Тест с iPerf3
```

**Задача 2: Wi-Fi 6 анализ (8 мин)**

```
WiFi Analyzer задачи:
1. Сканиране на мрежи
2. Идентифициране на:
   - Wi-Fi генерация
   - Channel width
   - Signal strength
   - Channel overlap

3. Оптимален канал избор
4. Измерване на real throughput
```

**Задача 3: Сравнителен тест (7 мин)**

Направете таблица със сравнение:

| Метрика | 1 Gbps Ethernet | 10G Ethernet | Wi-Fi 5 | Wi-Fi 6 |
|---------|-----------------|--------------|---------|---------|
| Throughput | | | | |
| Latency | | | | |
| Jitter | | | | |
| CPU usage | | | | |

### **5. ОБОБЩЕНИЕ (8 минути)**

**Ключови изводи:**
- 10G Ethernet става достъпен за prosumer
- Wi-Fi 6 решава density проблемите
- Правилната инфраструктура е критична
- Бъдещето: 25G/100G Ethernet, Wi-Fi 7

**Use cases:**
```
10G Ethernet подходящ за:
- NAS/SAN системи
- Video editing
- Virtualization hosts
- Backbone connections

Wi-Fi 6/6E подходящ за:
- High-density среди
- IoT deployments  
- AR/VR applications
- Mobile devices
```

### **6. ДОМАШНА РАБОТА (2 минути)**

**Задачи:**

1. **Проектна задача:**
   - Проектирайте мрежа за малък офис (50 души)
   - Включете 10G backbone и Wi-Fi 6
   - Диаграма + спецификации + цени

2. **Изследователска:**
   - Сравнете Wi-Fi 6 vs Wi-Fi 7
   - Кога си заслужава upgrade?
   - 2-3 страници анализ

3. **Практическа:**
   - Тествайте домашната Wi-Fi мрежа
   - Измерете coverage и speed
   - Предложете подобрения

**Срок:** До следващия учебен час

---

## 6. ОЦЕНЯВАНЕ

### КРИТЕРИИ ЗА ОЦЕНЯВАНЕ:

| Критерий | Точки |
|----------|-------|
| Познаване на стандарти | 25% |
| Разбиране на технологии | 25% |
| Практическа конфигурация | 20% |
| Анализ на резултати | 15% |
| Решаване на проблеми | 10% |
| Активност | 5% |

### ОЦЕНЪЧНА РУБРИКА:
- **Отличен (6):** Детайлно познава стандартите, конфигурира и оптимизира
- **Много добър (5):** Добро разбиране, успешна базова конфигурация
- **Добър (4):** Основни познания, нуждае се от помощ при setup
- **Среден (3):** Минимални знания, затруднения с практическата част

---

## 7. РЕФЛЕКСИЯ И АНАЛИЗ

### ВЪПРОСИ ЗА САМООЦЕНКА:
1. Разбирам ли кога да използвам 10G vs 1G?
2. Мога ли да планирам Wi-Fi покритие?
3. Знам ли как да troubleshoot мрежови проблеми?
4. Готов ли съм да проектирам мрежа?

### ИНДИКАТОРИ ЗА УСПЕХ:
- [ ] 90% разбират разликите между технологиите
- [ ] 85% могат да конфигурират basic setup
- [ ] 80% интерпретират правилно тестовете
- [ ] 75% предлагат подходящи решения

---

## 8. ПРИЛОЖЕНИЯ

### ПРИЛОЖЕНИЕ 1: МРЕЖОВИ СТАНДАРТИ

**Ethernet PHY спецификации:**
```
Standard    | Media        | Distance | Power
------------|--------------|----------|-------
10GBASE-T   | Cat6a/7      | 100m     | 6-10W
10GBASE-SR  | MMF OM3/4    | 300/400m | 1W
10GBASE-LR  | SMF OS1/2    | 10km     | 1W
10GBASE-CR  | Twinax       | 7m       | 0.5W

25GBASE-T   | Cat8         | 30m      | 8W
25GBASE-SR  | MMF OM4      | 100m     | 1.5W
25GBASE-CR  | Twinax       | 5m       | 0.5W

40GBASE-T   | Cat8         | 30m      | 15W
40GBASE-SR4 | MPO/MTP MMF  | 150m     | 1.5W
40GBASE-LR4 | SMF          | 10km     | 3.5W
```

### ПРИЛОЖЕНИЕ 2: WI-FI КАНАЛИ

**Channel allocation:**
```
2.4 GHz (802.11b/g/n/ax):
Ch 1:  2412 MHz
Ch 6:  2437 MHz  
Ch 11: 2462 MHz
(20 MHz spacing, 22 MHz width)

5 GHz (802.11a/n/ac/ax):
UNII-1: Ch 36-48 (5.180-5.240 GHz)
UNII-2A: Ch 52-64 (5.260-5.320 GHz) DFS
UNII-2C: Ch 100-144 (5.500-5.720 GHz) DFS
UNII-3: Ch 149-165 (5.745-5.825 GHz)

6 GHz (802.11ax/be):
UNII-5: Ch 1-93 (5.925-6.425 GHz)
UNII-6: Ch 95-117 (6.435-6.525 GHz)
UNII-7: Ch 119-181 (6.535-6.875 GHz)
UNII-8: Ch 183-233 (6.885-7.125 GHz)
```

### ПРИЛОЖЕНИЕ 3: КОНФИГУРАЦИОННИ КОМАНДИ

**Linux 10G optimization:**
```bash
# Interface settings
ethtool -G eth0 rx 4096 tx 4096
ethtool -K eth0 gro on tso on

# Interrupt affinity
for i in $(grep eth0 /proc/interrupts | awk '{print $1}' | sed 's/://'); do
  echo 4 > /proc/irq/$i/smp_affinity
done

# Kernel parameters
echo 'net.core.rmem_max = 134217728' >> /etc/sysctl.conf
echo 'net.core.wmem_max = 134217728' >> /etc/sysctl.conf
echo 'net.ipv4.tcp_rmem = 4096 87380 134217728' >> /etc/sysctl.conf
echo 'net.ipv4.tcp_wmem = 4096 65536 134217728' >> /etc/sysctl.conf
sysctl -p
```

**Wi-Fi debugging:**
```bash
# Linux
iw dev wlan0 scan
iw dev wlan0 station dump
iw dev wlan0 survey dump

# Windows PowerShell
netsh wlan show profiles
netsh wlan show interfaces
Get-NetAdapter | Where-Object {$_.Name -like "*Wi-Fi*"} | Get-NetAdapterStatistics
```

---

**Изготвил:** [Име на учителя]  
**Дата на изготвяне:** Декември 2024 г.
