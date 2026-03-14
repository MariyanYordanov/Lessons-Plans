# УРОЧЕН ПЛАН №24
## УЧЕБНА ПРАКТИКА: КОМПЮТЪРНИ АРХИТЕКТУРИ И ОПЕРАЦИОННИ СИСТЕМИ
### XII КЛАС

---

## 1. ОСНОВНИ ДАННИ

| Параметър | Стойност |
|-----------|----------|
| **Училище:** | 128-мо СУ "Алберт Айнщайн", гр.София |
| **Клас:** | XII клас |
| **Учител:** | Мариян Йорданов |
| **Предмет:** | Учебна практика: Компютърни архитектури и операционни системи |
| **Тема на урока:** | DNS и DHCP услуги в Windows Server |
| **Дата:** | ____________ |
| **Продължителност:** | 90 минути (2 учебни часа) |
| **Тип урок:** | Упражнение |
| **Място на провеждане:** | Компютърен кабинет |

---

## 2. ЦЕЛИ И ЗАДАЧИ

### ОБРАЗОВАТЕЛНИ ЦЕЛИ:
1. Учениците да разберат принципите на DNS резолюция
2. Да усвоят конфигурирането на DHCP сървър
3. Да създават DNS зони и записи
4. Да конфигурират DHCP scopes и опции
5. Да интегрират DNS и DHCP с Active Directory

### ВЪЗПИТАТЕЛНИ ЦЕЛИ:
1. Формиране на разбиране за мрежова инфраструктура
2. Развиване на систематичен подход при конфигуриране
3. Изграждане на отговорност при управление на критични услуги
4. Насърчаване на внимание към детайлите

### РАЗВИВАЩИ ЦЕЛИ:
1. Развитие на умения за мрежово планиране
2. Усъвършенстване на troubleshooting умения
3. Формиране на способност за документиране на конфигурации
4. Развитие на логическо мислене при диагностика

---

## 3. СЪДЪРЖАНИЕ

### ОСНОВНИ ЗНАНИЯ:

**DNS (Domain Name System):**
- Йерархия на DNS (root, TLD, authoritative)
- Типове DNS записи (A, AAAA, CNAME, MX, PTR, SRV, TXT)
- Forward и Reverse lookup зони
- DNS резолюция процес
- Интеграция с Active Directory

**DHCP (Dynamic Host Configuration Protocol):**
- DORA процес (Discover, Offer, Request, Acknowledge)
- DHCP Scopes и опции
- Reservations и exclusions
- Lease времена
- DHCP Failover

### ОСНОВНИ УМЕНИЯ:
- Инсталиране на DNS и DHCP роли
- Създаване на DNS зони и записи
- Конфигуриране на DHCP scopes
- Диагностика на DNS/DHCP проблеми

### МЕЖДУПРЕДМЕТНИ ВРЪЗКИ:
1. **Мрежови технологии** - IP адресиране, подмрежи
2. **Информационна сигурност** - DNS Security, DHCP Snooping
3. **Английски език** - техническа документация
4. **Математика** - изчисления на IP диапазони

---

## 4. МЕТОДИ И СРЕДСТВА

### МЕТОДИ НА ПРЕПОДАВАНЕ:
1. Демонстрация на конфигурация
2. Практическа работа стъпка по стъпка
3. Лабораторни упражнения
4. Troubleshooting сценарии
5. Групова дискусия

### УЧЕБНИ СРЕДСТВА И МАТЕРИАЛИ:
- Windows Server 2022 VM в лабораторна среда
- Клиентски Windows 11 VM
- Работни листове (Приложение 1)
- Схеми на DNS/DHCP архитектура
- PowerShell команди (Приложение 2)

---

## 5. ХОД НА УРОКА

### **1. ОРГАНИЗАЦИОНЕН МОМЕНТ (5 минути)**

**Въведение:**
- Проверка на присъстващите
- Стартиране на лабораторната среда
- Представяне на целите

**Мотивация:**
"Всеки път когато въвеждате адрес в браузъра, DNS го превръща в IP. DHCP автоматично конфигурира вашия компютър. Тези услуги са гръбнакът на всяка мрежа."

---

### **2. АКТУАЛИЗАЦИЯ (8 минути)**

**Преговор:**
```
Въпроси:
1. Какво е IP адрес и защо ни трябва DNS?
2. Как компютърът получава IP адрес автоматично?
3. Каква е връзката между AD и DNS?
```

**Схема на DNS резолюция:**
```
Потребител въвежда: www.example.com

┌─────────────┐    1. Query    ┌─────────────┐
│   Client    │ ────────────► │  Local DNS  │
│  Computer   │               │   Server    │
└─────────────┘               └──────┬──────┘
       ▲                             │
       │                      2. Recursive
       │                         Query
       │                             │
       │                             ▼
       │                      ┌─────────────┐
       │                      │  Root DNS   │
       │                      │   Server    │
       │                      └──────┬──────┘
       │                             │
       │                      3. Referral
       │                             │
       │                             ▼
       │                      ┌─────────────┐
       │                      │   TLD DNS   │
       │                      │   (.com)    │
       │                      └──────┬──────┘
       │                             │
       │                      4. Referral
       │                             │
       │                             ▼
       │                      ┌─────────────┐
       │     6. Response      │Authoritative│
       └──────────────────────│    DNS      │
                              └─────────────┘
                              5. Answer: 93.184.216.34
```

---

### **3. НОВ МАТЕРИАЛ И ПРАКТИКА (55 минути)**

#### **Част 1: Инсталиране на DNS роля (10 минути)**

**PowerShell инсталация:**
```powershell
# Инсталиране на DNS Server роля
Install-WindowsFeature -Name DNS -IncludeManagementTools

# Проверка на инсталацията
Get-WindowsFeature DNS

# Отваряне на DNS Manager
dnsmgmt.msc
```

**GUI метод:**
```
Server Manager → Add Roles and Features
→ DNS Server → Install
```

#### **Част 2: Създаване на DNS зони (15 минути)**

**Практическа задача 2.1: Forward Lookup Zone**

```powershell
# Създаване на Primary Forward Zone
Add-DnsServerPrimaryZone -Name "lab.local" `
    -ZoneFile "lab.local.dns" `
    -DynamicUpdate Secure

# Или AD-интегрирана зона (препоръчително)
Add-DnsServerPrimaryZone -Name "lab.local" `
    -ReplicationScope Domain `
    -DynamicUpdate Secure
```

**Практическа задача 2.2: DNS записи**

```powershell
# A запис (IPv4)
Add-DnsServerResourceRecordA -ZoneName "lab.local" `
    -Name "server1" -IPv4Address "192.168.1.10"

# CNAME запис (alias)
Add-DnsServerResourceRecordCName -ZoneName "lab.local" `
    -Name "www" -HostNameAlias "server1.lab.local"

# MX запис (mail)
Add-DnsServerResourceRecordMX -ZoneName "lab.local" `
    -Name "." -MailExchange "mail.lab.local" -Preference 10

# Проверка на записите
Get-DnsServerResourceRecord -ZoneName "lab.local"
```

**Типове DNS записи:**

| Тип | Описание | Пример |
|-----|----------|--------|
| A | IPv4 адрес | server1 → 192.168.1.10 |
| AAAA | IPv6 адрес | server1 → 2001:db8::1 |
| CNAME | Alias | www → server1.lab.local |
| MX | Mail server | mail.lab.local, priority 10 |
| PTR | Reverse lookup | 10 → server1.lab.local |
| SRV | Service location | _ldap._tcp → dc1.lab.local |
| TXT | Text информация | SPF, DKIM записи |

**Практическа задача 2.3: Reverse Lookup Zone**

```powershell
# Създаване на Reverse Zone
Add-DnsServerPrimaryZone -NetworkId "192.168.1.0/24" `
    -ReplicationScope Domain `
    -DynamicUpdate Secure

# PTR запис
Add-DnsServerResourceRecordPtr -ZoneName "1.168.192.in-addr.arpa" `
    -Name "10" -PtrDomainName "server1.lab.local"
```

---

#### **Част 3: Инсталиране и конфигуриране на DHCP (20 минути)**

**Практическа задача 3.1: Инсталация на DHCP**

```powershell
# Инсталиране на DHCP роля
Install-WindowsFeature -Name DHCP -IncludeManagementTools

# Авторизиране на DHCP сървър в AD
Add-DhcpServerInDC -DnsName "dc1.lab.local" -IPAddress 192.168.1.10

# Създаване на security groups
netsh dhcp add securitygroups

# Рестартиране на услугата
Restart-Service DHCPServer
```

**Практическа задача 3.2: Създаване на DHCP Scope**

```powershell
# Създаване на scope
Add-DhcpServerv4Scope -Name "Lab Network" `
    -StartRange 192.168.1.100 `
    -EndRange 192.168.1.200 `
    -SubnetMask 255.255.255.0 `
    -State Active `
    -LeaseDuration 8:00:00:00

# Добавяне на опции към scope
Set-DhcpServerv4OptionValue -ScopeId 192.168.1.0 `
    -Router 192.168.1.1 `
    -DnsServer 192.168.1.10 `
    -DnsDomain "lab.local"

# Exclusion range (за статични IP)
Add-DhcpServerv4ExclusionRange -ScopeId 192.168.1.0 `
    -StartRange 192.168.1.1 -EndRange 192.168.1.50

# Резервация за конкретен клиент
Add-DhcpServerv4Reservation -ScopeId 192.168.1.0 `
    -IPAddress 192.168.1.101 `
    -ClientId "00-15-5D-01-02-03" `
    -Name "Printer1" `
    -Description "Network Printer"
```

**DHCP Scope визуализация:**
```
192.168.1.0/24 Network
├── 192.168.1.1-50      [EXCLUDED - Servers/Static]
├── 192.168.1.51-99     [Available for future use]
├── 192.168.1.100-200   [DHCP SCOPE - Dynamic]
│   ├── 192.168.1.101   [RESERVED - Printer1]
│   └── 192.168.1.102+  [Available for clients]
└── 192.168.1.201-254   [Available for future use]
```

**Практическа задача 3.3: DHCP Options**

```powershell
# Преглед на всички опции
Get-DhcpServerv4OptionDefinition

# Важни опции:
# Option 3  - Router (Default Gateway)
# Option 6  - DNS Servers
# Option 15 - DNS Domain Name
# Option 44 - WINS Servers
# Option 66 - TFTP Server (PXE boot)
# Option 67 - Boot file name

# Server-level опции
Set-DhcpServerv4OptionValue -DnsDomain "lab.local" `
    -DnsServer 192.168.1.10,8.8.8.8

# Scope-specific опции
Set-DhcpServerv4OptionValue -ScopeId 192.168.1.0 `
    -OptionId 66 -Value "192.168.1.20"
```

---

#### **Част 4: Тестване и диагностика (10 минути)**

**Практическа задача 4.1: DNS тестове**

```powershell
# nslookup
nslookup server1.lab.local
nslookup 192.168.1.10

# Resolve-DnsName (PowerShell)
Resolve-DnsName -Name "server1.lab.local" -Type A
Resolve-DnsName -Name "lab.local" -Type MX

# Изчистване на DNS кеш
Clear-DnsClientCache
ipconfig /flushdns

# Показване на DNS кеш
Get-DnsClientCache
```

**Практическа задача 4.2: DHCP тестове**

```powershell
# На клиента - освобождаване и подновяване
ipconfig /release
ipconfig /renew
ipconfig /all

# На сървъра - преглед на leases
Get-DhcpServerv4Lease -ScopeId 192.168.1.0

# Статистика
Get-DhcpServerv4ScopeStatistics -ScopeId 192.168.1.0
```

---

### **4. ЗАТВЪРЖДАВАНЕ (12 минути)**

**Задача за самостоятелна работа:**

| Задача | Описание |
|--------|----------|
| 1 | Създайте A запис за "fileserver" с IP 192.168.1.20 |
| 2 | Създайте CNAME "files" сочещ към fileserver.lab.local |
| 3 | Добавете DHCP резервация за работна станция |
| 4 | Тествайте DNS резолюция с nslookup |

**Въпроси за дискусия:**
1. Защо е важна интеграцията на DNS с AD?
2. Кога използваме DHCP reservations вместо static IP?
3. Какво се случва ако DHCP сървърът е недостъпен?

---

### **5. ОБОБЩЕНИЕ (8 минути)**

**Ключови точки:**
```
DNS:
✓ Превежда имена в IP адреси
✓ Forward и Reverse зони
✓ A, CNAME, MX, PTR записи
✓ Интеграция с Active Directory

DHCP:
✓ Автоматично IP конфигуриране
✓ DORA процес
✓ Scopes, Exclusions, Reservations
✓ Options за gateway, DNS, domain
```

---

### **6. ДОМАШНА РАБОТА (2 минути)**

```
1. Документирайте DNS зоните и записите от упражнението

2. Създайте схема на DHCP scope с:
   - Network: 10.0.0.0/24
   - Gateway: 10.0.0.1
   - DNS: 10.0.0.10
   - DHCP range: 10.0.0.100-200
   - 3 резервации

3. Отговорете: Какво е DNS forwarder и кога се използва?

Време: 30-40 минути
```

---

## 6. ОЦЕНЯВАНЕ

| Компонент | Точки | Процент |
|-----------|-------|---------|
| DNS зона и записи | 25 | 35% |
| DHCP scope конфигурация | 25 | 35% |
| Тестове и диагностика | 15 | 20% |
| Домашна работа | 5 | 10% |
| **ОБЩО** | **70** | **100%** |

---

## 7. РЕФЛЕКСИЯ И АНАЛИЗ

### ВЪПРОСИ ЗА САМООЦЕНКА:
1. Мога ли да създам DNS зона самостоятелно?
2. Разбирам ли DHCP scope конфигурацията?
3. Мога ли да диагностицирам DNS/DHCP проблеми?

### ИНДИКАТОРИ ЗА УСПЕХ:
- [ ] 85% създават DNS зони правилно
- [ ] 80% конфигурират DHCP scope
- [ ] 75% успешно тестват услугите

---

## 8. ПРИЛОЖЕНИЯ

### ПРИЛОЖЕНИЕ 1: РАБОТЕН ЛИСТ

```
╔════════════════════════════════════════════════════════════╗
║        РАБОТЕН ЛИСТ: DNS И DHCP КОНФИГУРАЦИЯ              ║
╠════════════════════════════════════════════════════════════╣
║ Име: _______________________ Клас: ______ Дата: _________ ║
╚════════════════════════════════════════════════════════════╝

ЗАДАЧА 1: DNS КОНФИГУРАЦИЯ

Създадена Forward Zone: _______________________________

DNS записи:
| Име | Тип | Стойност |
|-----|-----|----------|
|     |     |          |
|     |     |          |
|     |     |          |

Reverse Zone: __________________________________________

ЗАДАЧА 2: DHCP КОНФИГУРАЦИЯ

Scope Name: ____________________________________________
IP Range: _____________________________________________
Subnet Mask: __________________________________________
Default Gateway: ______________________________________
DNS Server: ___________________________________________
Lease Duration: _______________________________________

Exclusions: ___________________________________________
Reservations: _________________________________________

ЗАДАЧА 3: ТЕСТВАНЕ

nslookup резултат:
___________________________________________________

ipconfig /all резултат (IP от DHCP):
___________________________________________________

═══════════════════════════════════════════════════════════
```

### ПРИЛОЖЕНИЕ 2: POWERSHELL КОМАНДИ

```powershell
# ══════════════════════════════════════════════════════════
#              DNS/DHCP POWERSHELL СПРАВОЧНИК
# ══════════════════════════════════════════════════════════

# DNS КОМАНДИ
# ─────────────────────────────────────────

# Инсталация
Install-WindowsFeature DNS -IncludeManagementTools

# Зони
Get-DnsServerZone
Add-DnsServerPrimaryZone -Name "domain.local" -ReplicationScope Domain
Remove-DnsServerZone -Name "domain.local"

# Записи
Get-DnsServerResourceRecord -ZoneName "domain.local"
Add-DnsServerResourceRecordA -ZoneName "domain.local" -Name "host" -IPv4Address "10.0.0.1"
Remove-DnsServerResourceRecord -ZoneName "domain.local" -Name "host" -RRType A

# Диагностика
Resolve-DnsName "hostname.domain.local"
Clear-DnsServerCache

# DHCP КОМАНДИ
# ─────────────────────────────────────────

# Инсталация
Install-WindowsFeature DHCP -IncludeManagementTools
Add-DhcpServerInDC

# Scopes
Get-DhcpServerv4Scope
Add-DhcpServerv4Scope -Name "Scope1" -StartRange 10.0.0.100 -EndRange 10.0.0.200 -SubnetMask 255.255.255.0
Remove-DhcpServerv4Scope -ScopeId 10.0.0.0

# Options
Get-DhcpServerv4OptionValue -ScopeId 10.0.0.0
Set-DhcpServerv4OptionValue -ScopeId 10.0.0.0 -Router 10.0.0.1 -DnsServer 10.0.0.10

# Leases
Get-DhcpServerv4Lease -ScopeId 10.0.0.0

# Reservations
Add-DhcpServerv4Reservation -ScopeId 10.0.0.0 -IPAddress 10.0.0.101 -ClientId "AA-BB-CC-DD-EE-FF"

# ══════════════════════════════════════════════════════════
```

---

*Документът е създаден за учебната 2025/2026 година*
*Специалност: Икономическо информационно осигуряване (код 482021)*
