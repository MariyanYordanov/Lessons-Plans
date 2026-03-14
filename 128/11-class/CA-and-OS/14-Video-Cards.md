# УРОЧЕН ПЛАН №14
## УЧЕБНА ПРАКТИКА: КОМПЮТЪРНИ АРХИТЕКТУРИ И ОПЕРАЦИОННИ СИСТЕМИ
### XI КЛАС

---

## 1. ОСНОВНИ ДАННИ

- **Училище:** 128-мо СУ "Алберт Айнщайн", гр.София
- **Клас:** XI клас
- **Предмет:** Учебна практика: Компютърни архитектури и операционни системи
- **Тема на урока:** Видове видеокарти и техните характеристики
- **Дата:** ____________
- **Час:** ____________
- **Продължителност:** 90 минути (2 учебни часа)
- **Тип урок:** Нови знания
- **Място на провеждане:** Компютърен кабинет

---

## 2. ЦЕЛИ И ЗАДАЧИ

### ОБРАЗОВАТЕЛНИ ЦЕЛИ:
1. Учениците да разберат функцията и архитектурата на видеокартите
2. Да усвоят различията между integrated и dedicated GPU
3. Да познават основните характеристики и параметри
4. Да разбират видовете памет и интерфейси
5. Да могат да избират подходяща видеокарта според нуждите

### ВЪЗПИТАТЕЛНИ ЦЕЛИ:
1. Формиране на разбиране за визуалните технологии
2. Възпитаване на критично мислене при избор на хардуер
3. Развиване на интерес към компютърна графика
4. Изграждане на технически усет за качество

### РАЗВИВАЩИ ЦЕЛИ:
1. Развитие на умения за анализ на спецификации
2. Усъвършенстване на способности за сравнение
3. Формиране на умения за оценка на производителност
4. Развитие на визуална култура

---

## 3. СЪДЪРЖАНИЕ

### ОСНОВНИ ЗНАНИЯ И УМЕНИЯ:

#### Знания:
- GPU архитектура и компоненти
- Integrated vs Discrete graphics
- NVIDIA vs AMD vs Intel Arc
- Видеопамет: GDDR6, GDDR6X, HBM
- Интерфейси: PCIe, DisplayPort, HDMI
- Ray Tracing, DLSS, FSR технологии

#### Умения:
- Разчитане на GPU спецификации
- Сравнение на видеокарти
- Избор според употреба (gaming, работа, mining)
- Разпознаване на различни модели
- Основна диагностика на проблеми

### ВРЪЗКИ С ДРУГИ ПРЕДМЕТИ:

1. **Физика** - оптика, светлина, цветове
2. **Математика** - матрични операции, 3D геометрия
3. **Информатика** - компютърна графика, рендериране
4. **Изобразително изкуство** - цветови модели, композиция
5. **Икономика** - price/performance анализ

---

## 4. МЕТОДИ И СРЕДСТВА

### МЕТОДИ НА ПРЕПОДАВАНЕ:
1. **Интерактивна презентация** с визуални материали
2. **Демонстрация** на различни видеокарти
3. **Практическа работа** с диагностичен софтуер
4. **Сравнителен анализ** на модели
5. **Видео демонстрации** на технологии

### УЧЕБНИ СРЕДСТВА И МАТЕРИАЛИ:
1. **Хардуер:**
   - Различни видеокарти за демонстрация
   - Компютри с различни GPU
   
2. **Софтуер:**
   - GPU-Z
   - MSI Afterburner
   - 3DMark
   - FurMark
   - HWiNFO64
   
3. **Учебни материали:**
   - Блок-схеми на GPU архитектура
   - Сравнителни таблици
   - Benchmark резултати

---

## 5. ХОД НА УРОКА

### **1. ОРГАНИЗАЦИОНЕН МОМЕНТ (5 минути)**

**Дейност на учителя:**
- Проверка на присъствието
- Подготовка на демонстрационните материали
- Въвеждащ въпрос: "Защо игрите изискват мощни видеокарти?"

**Дейност на учениците:**
- Подготовка за урока
- Споделяне на опит с видеокарти

### **2. АКТУАЛИЗАЦИЯ НА ЗНАНИЯТА (8 минути)**

**Дейност на учителя:**
- Преговор на компютърна архитектура

**Въпроси за преговор:**
1. Каква е функцията на видеокартата?
2. Какво е резолюция и refresh rate?
3. Какви видео изходи познавате?
4. Защо 3D графиката е "тежка"?

**Кратка демонстрация:**
- Разлика между integrated и dedicated graphics
- Task Manager → Performance → GPU usage

### **3. НОВ МАТЕРИАЛ (45 минути)**

#### **Част 1: GPU архитектура и принцип (12 мин)**

**Какво е GPU (Graphics Processing Unit):**
```
GPU = Specialized processor for:
- Rendering graphics
- Parallel computations
- Video encoding/decoding
- AI/ML acceleration

CPU vs GPU:
CPU: 4-24 complex cores
GPU: 1000s of simple cores

CPU: Sequential processing
GPU: Massive parallel processing
```

**GPU компоненти:**
```
┌─────────────────────────────────┐
│          GPU Die                 │
├─────────────────────────────────┤
│ ┌─────────┐  ┌────────────────┐ │
│ │Streaming │  │ Raster Units   │ │
│ │Multiproc.│  │ (ROPs)         │ │
│ └─────────┘  └────────────────┘ │
│ ┌─────────┐  ┌────────────────┐ │
│ │ Texture │  │ RT Cores       │ │
│ │  Units  │  │ (NVIDIA)       │ │
│ └─────────┘  └────────────────┘ │
│ ┌─────────────────────────────┐ │
│ │    Memory Controller        │ │
│ └─────────────────────────────┘ │
└─────────────────────────────────┘
           ↓
    ┌─────────────┐
    │  VRAM Memory │
    └─────────────┘
```

**Ключови термини:**
```
Shaders/CUDA Cores/Stream Processors:
- Основни изчислителни единици
- NVIDIA: CUDA cores
- AMD: Stream processors
- Intel: Xe cores

ROPs (Render Output Units):
- Final pixel output
- Anti-aliasing
- Влияе на fill rate

TMUs (Texture Mapping Units):
- Texture filtering
- Texture addressing

RT Cores (Ray Tracing):
- Hardware ray tracing
- Realistic lighting
- Reflections/shadows
```

**Integrated vs Dedicated Graphics:**
```
Integrated Graphics (iGPU):
- Part of CPU (Intel UHD, AMD Vega)
- Shares system RAM
- Lower power (5-25W)
- Basic tasks, light gaming
- No extra cost

Dedicated Graphics (dGPU):
- Separate card
- Own VRAM (4-24GB)
- High power (75-450W)
- Gaming, professional work
- Additional cost

Hybrid Graphics:
- Laptop switchable graphics
- Optimus (NVIDIA) / Enduro (AMD)
- Power saving + performance
```

#### **Част 2: Производители и серии (13 мин)**

**NVIDIA GeForce:**
```
Current Generation (2024-2025):
RTX 40 Series (Ada Lovelace):
- RTX 4090: Flagship, 24GB
- RTX 4080: High-end, 16GB
- RTX 4070 Ti: Upper mid, 12GB
- RTX 4070: Mid-range, 12GB
- RTX 4060 Ti: Lower mid, 8/16GB
- RTX 4060: Entry gaming, 8GB

Naming scheme:
- First digit: Generation (4 = 40 series)
- Second digits: Performance tier (90=top)
- Ti/Super: Enhanced versions

Technologies:
- Ray Tracing (RT cores)
- DLSS 3 (AI upscaling)
- Frame Generation
- AV1 encoding
```

**AMD Radeon:**
```
Current Generation:
RX 7000 Series (RDNA 3):
- RX 7900 XTX: Flagship, 24GB
- RX 7900 XT: High-end, 20GB
- RX 7800 XT: Upper mid, 16GB
- RX 7700 XT: Mid-range, 12GB
- RX 7600: Entry, 8GB

Technologies:
- FSR 3 (FidelityFX Super Resolution)
- Ray Accelerators
- Infinity Cache
- Smart Access Memory
```

**Intel Arc:**
```
First Generation (Alchemist):
- Arc A770: Top tier, 16GB
- Arc A750: Mid-tier, 8GB
- Arc A580: Lower mid, 8GB
- Arc A380: Entry, 6GB

Technologies:
- XeSS (AI upscaling)
- AV1 hardware encode
- Ray Tracing
- Deep Link
```

**Professional cards:**
```
NVIDIA Quadro/RTX:
- RTX 6000 Ada: 48GB
- RTX A5000: 24GB
- CAD/3D modeling
- Certified drivers

AMD Radeon Pro:
- W7900: 48GB
- W6800: 32GB
- Content creation
- ECC memory

Intel Arc Pro:
- A60/A40
- Media processing
- Budget professional
```

#### **Част 3: Видеопамет и интерфейси (10 мин)**

**Video Memory (VRAM):**
```
Types and Evolution:
GDDR5: 8 Gbps (older cards)
GDDR5X: 10-12 Gbps (GTX 1080)
GDDR6: 14-16 Gbps (current mainstream)
GDDR6X: 19-21 Gbps (high-end NVIDIA)
HBM2/HBM3: 600+ GB/s (datacenter)

Memory Bus Width:
- 128-bit: Entry level (RTX 4060)
- 192-bit: Mid-range
- 256-bit: Upper mid (RTX 4070 Ti)
- 320-bit: High-end (RTX 4080)
- 384-bit: Flagship (RTX 4090)

Bandwidth = (Memory Speed × Bus Width) / 8
Example RTX 4070:
21 Gbps × 192-bit / 8 = 504 GB/s
```

**VRAM Requirements:**
```
Resolution Impact:
1080p: 4-6GB minimum
1440p: 8-10GB recommended
4K: 12-16GB+ ideal

Game/App examples (Ultra settings):
- Fortnite: 4-6GB
- Cyberpunk 2077: 10-12GB
- Flight Simulator: 12-16GB
- AI Stable Diffusion: 8-12GB
- 3D Rendering: 16-24GB+
```

**Interfaces and Connections:**
```
PCIe Generations:
PCIe 3.0 x16: 16 GB/s
PCIe 4.0 x16: 32 GB/s
PCIe 5.0 x16: 64 GB/s

Power Connectors:
- PCIe slot: 75W max
- 6-pin PCIe: +75W
- 8-pin PCIe: +150W
- 12VHPWR: 600W (new standard)

Display Outputs:
DisplayPort 1.4: 4K@144Hz, 8K@60Hz
DisplayPort 2.1: 4K@240Hz, 16K@60Hz
HDMI 2.1: 4K@120Hz, 8K@60Hz
USB-C/Thunderbolt: Alt mode DP
```

#### **Част 4: Технологии и features (10 мин)**

**Ray Tracing:**
```
Traditional Rasterization:
- Fast but approximations
- Baked lighting
- Screen space reflections

Ray Tracing:
- Physically accurate light
- Real reflections/shadows
- Global illumination
- Very demanding (50% fps drop)
```

**Upscaling Technologies:**
```
NVIDIA DLSS (Deep Learning Super Sampling):
- AI-based upscaling
- Render at lower resolution
- Upscale with AI
- DLSS 3: Frame Generation
- 2-3x performance boost

AMD FSR (FidelityFX Super Resolution):
- Spatial upscaling
- Works on all GPUs
- FSR 3: Frame Generation
- 1.5-2x performance

Intel XeSS:
- AI upscaling
- DP4a fallback
- Cross-vendor support
```

**Performance Metrics:**
```
Key Specifications:
- Base/Boost Clock (MHz)
- CUDA/Stream cores
- Memory size/speed
- TDP (Power consumption)
- FP32 performance (TFLOPS)

Benchmarks:
- 3DMark Time Spy (DX12)
- Unigine Heaven (DX11)
- Real game FPS
- Professional apps (Blender, Premiere)
```

### **4. ЗАТВЪРЖДАВАНЕ (27 минути)**

#### **Практическа работа: Анализ и тестване**

**Задача 1: GPU-Z анализ (8 мин)**

```
Отворете GPU-Z и запишете:
1. GPU Name и Architecture
2. Process node (nm)
3. Die size (mm²)
4. Transistor count
5. Shaders/CUDA cores
6. TMUs и ROPs
7. Memory type и Bus width
8. Bandwidth
9. Current clocks vs Boost
10. Temperature и Power draw
```

**Таблица за попълване:**
| Параметър | Стойност | Нормално ли е? |
|-----------|----------|----------------|
| GPU | | |
| Memory | | |
| Temperature | | |
| Power Draw | | |

**Задача 2: Performance тестване (10 мин)**

```
FurMark Stress Test:
1. Resolution: 1920×1080
2. Run for 5 minutes
3. Monitor:
   - FPS
   - Temperature
   - Clock speeds
   - Power consumption

Внимание: Температури до 83°C са нормални!
```

**Задача 3: Конфигурационни сценарии (9 мин)**

Препоръчайте видеокарта за:

**A. Office PC:**
```
Нужди: Office, web, video
Бюджет: Минимален
Решение: Integrated graphics достатъчно
```

**B. 1080p Gaming:**
```
Нужди: 60+ FPS, High settings
Бюджет: 500 EUR
Решение: RTX 4060 / RX 7600
```

**C. Content Creation:**
```
Нужди: 4K editing, 3D rendering
Бюджет: 1500 EUR
Решение: RTX 4070 Ti / RX 7900 XT
```

**D. AI/ML Development:**
```
Нужди: CUDA, много VRAM
Бюджет: 2000 EUR
Решение: RTX 4090 (24GB VRAM)
```

### **5. ОБОБЩЕНИЕ (10 минути)**

**Ключови моменти:**
- GPU за паралелни изчисления
- Integrated достатъчно за офис
- VRAM важна за резолюция
- Ray Tracing = реализъм но performance cost
- DLSS/FSR помагат за performance

**Избор според нужди:**
```
Gaming:
1080p: RTX 4060, RX 7600
1440p: RTX 4070, RX 7800 XT
4K: RTX 4080+, RX 7900 XTX

Professional:
CAD: Quadro/Radeon Pro
Video: High VRAM cards
3D: RT cores useful
AI: NVIDIA CUDA dominant
```

### **6. ДОМАШНА РАБОТА (5 минути)**

**Задачи:**

1. **Изследователска:**
   - Сравнете RTX 4070 vs RX 7800 XT
   - Тестове, цени, features
   - Препоръка с обосновка
   - 2 страници

2. **Практическа:**
   - Проверете домашната видеокарта
   - GPU-Z screenshot
   - Benchmark резултат
   - Подходяща ли е за нуждите?

3. **Проектна:**
   - Конфигурирайте gaming PC
   - Балансирайте CPU и GPU
   - Останете в бюджет 2000 EUR
   - Обосновете избора

**Срок:** До следващия учебен час

---

## 6. ОЦЕНЯВАНЕ

### КРИТЕРИИ ЗА ОЦЕНЯВАНЕ:

| Критерий | Точки |
|----------|-------|
| Познаване на GPU архитектура | 25% |
| Разбиране на характеристики | 20% |
| Сравнителен анализ | 20% |
| Практическа работа с софтуер | 15% |
| Правилен избор за сценарии | 15% |
| Активност | 5% |

### ОЦЕНЪЧНА РУБРИКА:
- **Отличен (6):** Детайлно познава всички аспекти, прави точен анализ
- **Много добър (5):** Добро разбиране, правилни препоръки
- **Добър (4):** Основни познания, нуждае се от насочване
- **Среден (3):** Минимални знания, затруднения с терминология

---

## 7. РЕФЛЕКСИЯ И АНАЛИЗ

### ВЪПРОСИ ЗА САМООЦЕНКА:
1. Разбирам ли разликата между GPU и CPU?
2. Мога ли да чета GPU спецификации?
3. Знам ли кога коя видеокарта е подходяща?
4. Умея ли да диагностицирам GPU проблеми?

### ИНДИКАТОРИ ЗА УСПЕХ:
- [ ] 90% разбират GPU функцията
- [ ] 85% различават integrated/dedicated
- [ ] 80% могат да сравнят модели
- [ ] 75% правилно избират за нужди
- [ ] 70% използват диагностичен софтуер

---

## 8. ПРИЛОЖЕНИЯ

### ПРИЛОЖЕНИЕ 1: GPU СПЕЦИФИКАЦИИ 2025

**Current Generation Comparison:**
```
Model         | Cores | VRAM | TDP  | MSRP
--------------|-------|------|------|-------
RTX 4090      | 16384 | 24GB | 450W | $1599
RTX 4080      | 9728  | 16GB | 320W | $1199
RTX 4070 Ti   | 7680  | 12GB | 285W | $799
RTX 4070      | 5888  | 12GB | 200W | $599
RTX 4060 Ti   | 4352  | 8/16 | 160W | $399
RTX 4060      | 3072  | 8GB  | 115W | $299

RX 7900 XTX   | 6144  | 24GB | 355W | $999
RX 7900 XT    | 5376  | 20GB | 315W | $749
RX 7800 XT    | 3840  | 16GB | 263W | $499
RX 7700 XT    | 3456  | 12GB | 245W | $349
RX 7600       | 2048  | 8GB  | 165W | $269

Arc A770      | 4096  | 16GB | 225W | $349
Arc A750      | 3584  | 8GB  | 225W | $289
```

### ПРИЛОЖЕНИЕ 2: DIAGNOSTIC COMMANDS

**Windows:**
```cmd
# Device info
dxdiag

# GPU stress test
Windows + G → Performance

# Driver version
nvidia-smi (NVIDIA)
radeon-settings (AMD)
```

**GPU-Z важни стойности:**
```
Normal ranges:
- GPU Temp: 30-40°C idle, 70-83°C load
- Hot Spot: +10-15°C над GPU temp
- Memory Temp: <90°C
- Fan Speed: 30% idle, 50-70% load
- Power Draw: 10-30W idle, TDP load
```

### ПРИЛОЖЕНИЕ 3: TROUBLESHOOTING

**Чести проблеми:**
```
No Display:
- Проверете захранването
- Reseat картата
- Опитайте друг PCIe slot
- Clear CMOS

Artifacts/Crashes:
- Температура висока?
- Driver update/rollback
- Намалете clocks
- Проверете PSU

Low Performance:
- Power saving mode?
- Thermal throttling?
- CPU bottleneck?
- Wrong PCIe slot (x4 vs x16)

Coil Whine:
- Normal at high FPS
- Limit FPS
- Check PSU quality
```

---

**Изготвил:** [Име на учителя]  
**Дата на изготвяне:** Декември 2024 г.
