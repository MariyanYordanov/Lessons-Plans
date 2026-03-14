# УРОЧЕН ПЛАН №10
## УЧЕБНА ПРАКТИКА: КОМПЮТЪРНИ АРХИТЕКТУРИ И ОПЕРАЦИОННИ СИСТЕМИ
### XII КЛАС

---

## 1. ОСНОВНИ ДАННИ

- **Училище:** ПГИ „Професор д-р Асен Златаров"
- **Клас:** XII клас
- **Предмет:** Учебна практика: Компютърни архитектури и операционни системи
- **Тема на урока:** VMware vSphere - конфигурация на виртуални машини
- **Дата:** ____________
- **Час:** ____________
- **Продължителност:** 90 минути (2 учебни часа)
- **Тип урок:** Упражнение
- **Място на провеждане:** Компютърна лаборатория

---

## 2. ЦЕЛИ И ЗАДАЧИ

### ОБРАЗОВАТЕЛНИ ЦЕЛИ:
1. Учениците да овладеят създаването на VM в vSphere
2. Да усвоят конфигурирането на виртуален хардуер
3. Да научат управлението на VM lifecycle
4. Да разберат advanced настройките и оптимизации
5. Да могат да работят с snapshots и клониране

### ВЪЗПИТАТЕЛНИ ЦЕЛИ:
1. Формиране на професионални умения за виртуализация
2. Възпитаване на системен подход при конфигуриране
3. Развиване на отговорност при управление на ресурси
4. Изграждане на навици за документиране

### РАЗВИВАЩИ ЦЕЛИ:
1. Развитие на практически умения с enterprise софтуер
2. Усъвършенстване на troubleshooting способности
3. Формиране на умения за capacity planning
4. Развитие на административни компетенции

---

## 3. СЪДЪРЖАНИЕ

### ОСНОВНИ ЗНАНИЯ И УМЕНИЯ:

#### Знания:
- vSphere архитектура: vCenter, ESXi, vSphere Client
- Virtual hardware версии и съвместимост
- VM resource allocation: CPU, RAM, Storage
- Guest OS поддръжка и VMware Tools
- Snapshots, клониране и templates
- vMotion и Storage vMotion концепции

#### Умения:
- Създаване и конфигуриране на VM
- Инсталиране на Guest OS
- Управление на VM lifecycle
- Работа със snapshots
- Клониране и deployment от templates
- Performance мониторинг и оптимизация

### ВРЪЗКИ С ДРУГИ ПРЕДМЕТИ:

1. **Операционни системи** - инсталация и конфигурация
2. **Мрежова администрация** - virtual networking
3. **Системна администрация** - управление на сървъри
4. **Бази данни** - виртуализация на DB сървъри
5. **Информационна сигурност** - изолация и защита

---

## 4. МЕТОДИ И СРЕДСТВА

### МЕТОДИ НА ПРЕПОДАВАНЕ:
1. **Демонстрация** на vSphere интерфейса
2. **Практическа работа** със създаване на VMs
3. **Стъпка по стъпка** инструкции
4. **Проблемно обучение** с реални сценарии
5. **Работа в екипи** за сложни конфигурации

### УЧЕБНИ СРЕДСТВА И МАТЕРИАЛИ:
1. **Софтуер:**
   - VMware vSphere 8.0
   - vSphere Client (HTML5)
   - VMware Remote Console
   - ISO образи на различни OS
   
2. **Хардуер:**
   - ESXi сървър или nested virtualization
   - Достатъчно RAM и storage
   - Мрежова свързаност
   
3. **Учебни материали:**
   - vSphere документация
   - Best practices guides
   - Конфигурационни templates

---

## 5. ХОД НА УРОКА

### **1. ОРГАНИЗАЦИОНЕН МОМЕНТ (5 минути)**

**Дейност на учителя:**
- Проверка на присъствието
- Проверка на достъпа до vSphere среда
- Разпределение на ресурси за учениците

**Дейност на учениците:**
- Login в vSphere Client
- Проверка на assigned permissions
- Подготовка на ISO файлове

### **2. АКТУАЛИЗАЦИЯ НА ЗНАНИЯТА (8 минути)**

**Дейност на учителя:**
- Преговор на vSphere компоненти

**Въпроси за преговор:**
1. Каква е разликата между vCenter и ESXi?
2. Какво е virtual machine hardware version?
3. Защо са необходими VMware Tools?
4. Какво е thin vs thick provisioning?

**Кратка навигация:**
- vSphere Client интерфейс
- Hosts and Clusters view
- VMs and Templates view
- Storage и Network views

### **3. ПРАКТИЧЕСКА РАБОТА (65 минути)**

#### **Част 1: Създаване на нова VM (20 мин)**

**New Virtual Machine Wizard:**

**Step 1: Select creation type**
```
Options:
□ Create a new virtual machine
□ Deploy from template
□ Deploy from OVF/OVA
□ Clone existing VM

За упражнението: Create new VM
```

**Step 2: Name and folder**
```
VM Name: TestVM-Student01
Location: /Datacenter/vm/Training
Naming convention:
- Purpose-Owner-Number
- No spaces (use dash/underscore)
- Descriptive but concise
```

**Step 3: Compute resource**
```
Select destination:
├── Cluster-01
│   ├── ESXi-01 (60% used)
│   ├── ESXi-02 (40% used) ← Select
│   └── ESXi-03 (55% used)

Consider:
- Resource availability
- DRS recommendations
- Affinity rules
```

**Step 4: Storage**
```
Select datastore:
Name         | Type | Free    | Capacity
-------------|------|---------|----------
DS-SSD-01    | VMFS | 500GB   | 2TB
DS-HDD-01    | VMFS | 2TB     | 10TB
DS-NFS-01    | NFS  | 5TB     | 20TB

Storage policy: [Default]
Disk provisioning:
○ Thick Provision Lazy Zeroed
○ Thick Provision Eager Zeroed
● Thin Provision ← за lab среда
```

**Step 5: Compatibility**
```
VM Hardware Version:
- ESXi 8.0: Hardware version 20
- ESXi 7.0: Hardware version 18
- ESXi 6.7: Hardware version 14

Select: 18 (за съвместимост)
```

**Step 6: Guest OS**
```
Guest OS Family: 
- Windows
- Linux ← Select
- Other

Guest OS Version:
- Ubuntu Linux (64-bit) ← Select
- Red Hat Enterprise Linux
- SUSE Linux
- Other Linux
```

**Step 7: Customize hardware**
```
CPU Configuration:
- CPUs: 2
- Cores per Socket: 2
- CPU Hot Add: Disabled

Memory:
- RAM: 4 GB
- Memory Hot Add: Disabled
- Reservation: 0
- Limit: Unlimited

Hard Disk:
- Size: 20 GB
- Disk Provisioning: Thin
- Disk Mode: Dependent

Network:
- Network Adapter: VMXNET3
- Network: VM Network
- Connect at Power On: ✓

CD/DVD Drive:
- Datastore ISO File
- Browse: Ubuntu-22.04-server.iso
- Connect at Power On: ✓
```

#### **Част 2: Advanced конфигурация (15 мин)**

**VM Options настройки:**

**Boot Options:**
```
Firmware: BIOS or UEFI
- BIOS (legacy)
- UEFI (modern)
- UEFI Secure Boot

Boot Delay: 5000 ms
Force BIOS Setup: □
Boot Order:
1. CD-ROM Drive
2. Hard Disk
3. Network
```

**VMware Tools:**
```
Options:
✓ Check and upgrade Tools on power cycle
✓ Synchronize guest time with host
□ Enable VMCI (VM Communication Interface)

Tools Scripts:
- Power On: /usr/local/bin/startup.sh
- Shutdown: /usr/local/bin/shutdown.sh
- Suspend/Resume scripts
```

**Advanced Parameters:**
```
Configuration Parameters (examples):
tools.syncTime = "TRUE"
disk.EnableUUID = "TRUE"
isolation.tools.copy.disable = "FALSE"
mem.hotadd = "TRUE"
vcpu.hotadd = "TRUE"
svga.autodetect = "TRUE"
```

**Resource Allocation:**
```
CPU:
- Reservation: 0 MHz (guaranteed)
- Limit: Unlimited
- Shares: Normal (1000)

Memory:
- Reservation: 1024 MB
- Limit: Unlimited  
- Shares: Normal (40960)

Disk I/O:
- Shares: Normal (1000)
- Limit: Unlimited IOPS
```

#### **Част 3: Guest OS инсталация (10 мин)**

**Power On и Console:**
```
1. Right-click VM → Power → Power On
2. Open Remote Console (VMRC)
3. Boot от ISO
4. Follow OS installation:
   - Keyboard layout
   - Network configuration
   - Disk partitioning
   - User creation
   - Package selection
```

**VMware Tools инсталация:**
```
Linux:
# Mount VMware Tools ISO
VM → Guest OS → Install VMware Tools

# In guest:
sudo mount /dev/cdrom /mnt
tar -xzf /mnt/VMwareTools*.tar.gz
sudo ./vmware-tools-distrib/vmware-install.pl
# или
sudo apt-get install open-vm-tools

Windows:
- AutoRun от mounted ISO
- или D:\setup.exe
```

#### **Част 4: Snapshots и клониране (12 мин)**

**Snapshot Management:**

**Създаване на snapshot:**
```
Right-click VM → Snapshots → Take Snapshot

Name: BeforeUpdate-2024-12-20
Description: Clean OS install, before updates
□ Snapshot VM memory (за running VMs)
□ Quiesce guest file system (needs Tools)

Snapshot chain:
Base → Snap1 → Snap2 → Current
        ↓
      Snap1a
```

**Revert и Delete:**
```
Revert to Snapshot:
- Returns VM to snapshot state
- Current changes lost

Delete Snapshot:
- Consolidates changes
- Frees disk space
- Cannot undo

Delete All Snapshots:
- Commits all changes to base
```

**Клониране на VM:**
```
Right-click VM → Clone

Clone Options:
Name: TestVM-Clone01
Folder: /Training/Clones

Clone Type:
○ Create linked clone (shares base)
● Create full clone (independent)

Customization:
□ Customize OS (requires specification)
□ Power on after creation
```

**Templates:**
```
Convert to Template:
1. Prepare VM (generalize)
2. Right-click → Template → Convert
3. Cannot power on template

Deploy from Template:
- New VM from template
- Guest customization
- Multiple deployments
```

#### **Част 5: Monitoring и управление (8 мин)**

**Performance Monitoring:**
```
VM Performance Charts:
- CPU Usage (MHz, %)
- Memory Usage (MB, %)
- Disk I/O (KBps, IOPS)
- Network (Mbps)

Real-time (20 sec refresh)
Historical (5 min, hourly, daily)
```

**VM Operations:**
```
Power Operations:
- Power On/Off
- Suspend/Resume
- Reset (hard reset)
- Shut Down Guest (graceful)
- Restart Guest (graceful)

Console Access:
- Remote Console (VMRC)
- Web Console
- SSH (if configured)
```

**Migration:**
```
vMotion (licensed feature):
- Live migration
- Zero downtime
- Requirements:
  - Shared storage
  - Same network
  - Compatible CPUs

Storage vMotion:
- Move VM storage
- While running
- Different datastores
```

### **4. ЗАТВЪРЖДАВАНЕ (10 минути)**

#### **Практически задачи:**

**Задача 1: Създайте Windows VM**
```
Requirements:
- Windows Server 2022
- 4 vCPU, 8GB RAM
- 60GB disk
- 2 network adapters
- Install VMware Tools
```

**Задача 2: Snapshot testing**
```
1. Create snapshot "Clean"
2. Install software
3. Create snapshot "WithSoftware"  
4. Make changes
5. Revert to "Clean"
6. Verify state
```

**Задача 3: Performance check**
```
Monitor и документирайте:
- CPU Ready time
- Memory ballooning
- Disk latency
- Network drops
```

### **5. ОБОБЩЕНИЕ (7 минути)**

**Ключови моменти:**
- Правилно sizing на VMs
- Thin vs Thick provisioning избор
- Важността на VMware Tools
- Snapshot best practices (не повече от 3-5)
- Resource pools и reservations

**Best Practices:**
```
1. Install VMware Tools ALWAYS
2. Use VMXNET3 за network
3. Use Paravirtual SCSI за performance
4. Regular snapshots но не permanent
5. Monitor resource usage
6. Document VM purpose
7. Use naming conventions
8. Regular backups отделно от snapshots
```

### **6. ДОМАШНА РАБОТА (5 минути)**

**Задачи:**

1. **Проектна задача:**
   - Планирайте 3-tier application
   - Web, App, DB servers
   - Детайлна VM конфигурация
   - Resource calculations
   - Network diagram

2. **Изследователска:**
   - vSphere HA и DRS
   - Как работят?
   - Configuration requirements
   - Use cases

3. **Практическа:**
   - Deploy Linux LAMP stack
   - Document всички стъпки
   - Performance baseline
   - Optimization suggestions

**Срок:** До следващия учебен час

---

## 6. ОЦЕНЯВАНЕ

### КРИТЕРИИ ЗА ОЦЕНЯВАНЕ:

| Критерий | Точки |
|----------|-------|
| Успешно създаване на VM | 25% |
| Правилна конфигурация на ресурси | 20% |
| Guest OS инсталация | 15% |
| VMware Tools setup | 10% |
| Snapshot management | 15% |
| Клониране/Templates | 10% |
| Активност | 5% |

### ОЦЕНЪЧНА РУБРИКА:
- **Отличен (6):** Създава и конфигурира сложни VMs, оптимизира ресурси
- **Много добър (5):** Успешно създава VMs, разбира всички настройки
- **Добър (4):** Създава основни VMs, нуждае се от помощ при advanced
- **Среден (3):** Затруднения с конфигурацията, основни умения

---

## 7. РЕФЛЕКСИЯ И АНАЛИЗ

### ВЪПРОСИ ЗА САМООЦЕНКА:
1. Мога ли самостоятелно да създам VM?
2. Разбирам ли resource allocation?
3. Умея ли да работя със snapshots?
4. Готов ли съм да управлявам production VMs?

### ИНДИКАТОРИ ЗА УСПЕХ:
- [ ] 100% създават работеща VM
- [ ] 90% инсталират Guest OS успешно
- [ ] 85% конфигурират VMware Tools
- [ ] 80% правилно използват snapshots
- [ ] 75% могат да клонират и templatize

---

## 8. ПРИЛОЖЕНИЯ

### ПРИЛОЖЕНИЕ 1: VM SIZING GUIDELINES

**Standard VM Sizes:**
```
Small VM:
- vCPU: 1-2
- RAM: 2-4 GB
- Disk: 20-40 GB
- Use: Basic services, testing

Medium VM:
- vCPU: 2-4  
- RAM: 4-8 GB
- Disk: 40-100 GB
- Use: Application servers

Large VM:
- vCPU: 4-8
- RAM: 16-32 GB
- Disk: 100-500 GB
- Use: Databases, heavy apps

XLarge VM:
- vCPU: 8+
- RAM: 32+ GB
- Disk: 500+ GB
- Use: Big data, analytics
```

**vCPU to pCPU Ratios:**
```
Environment  | Ratio | Example
-------------|-------|----------
Development  | 10:1  | 10 vCPUs per core
Test         | 6:1   | 6 vCPUs per core
Production   | 4:1   | 4 vCPUs per core
Critical     | 2:1   | 2 vCPUs per core
```

### ПРИЛОЖЕНИЕ 2: VMWARE TOOLS FEATURES

**Capabilities Enabled:**
```
Driver Optimizations:
- VMXNET3: Paravirtual network
- PVSCSI: Paravirtual SCSI
- VMware SVGA: Display driver

Guest Operations:
- Graceful shutdown/restart
- Time synchronization
- Heartbeat monitoring
- Guest customization

Enhanced Features:
- Shared folders (Workstation)
- Copy/paste between host/guest
- Drag and drop files
- Dynamic resolution
- Mouse integration

Performance:
- Memory ballooning
- Page sharing hints
- CPU/Memory hot-add
```

### ПРИЛОЖЕНИЕ 3: POWERCLI СКРИПТОВЕ

**Basic PowerCLI Commands:**
```powershell
# Connect to vCenter
Connect-VIServer vcenter.lab.local

# List all VMs
Get-VM

# Create new VM
New-VM -Name "TestVM" `
  -VMHost "esxi01.lab.local" `
  -Datastore "DS-SSD-01" `
  -DiskGB 20 `
  -MemoryGB 4 `
  -NumCPU 2

# Start VM
Start-VM -VM "TestVM"

# Take snapshot
New-Snapshot -VM "TestVM" `
  -Name "Backup" `
  -Description "Before updates"

# Clone VM
New-VM -Name "Clone01" `
  -VM "TestVM" `
  -VMHost "esxi02.lab.local" `
  -Datastore "DS-HDD-01"

# Get VM info
Get-VM "TestVM" | Select *

# Install VMware Tools
Get-VM "TestVM" | `
  Mount-Tools | `
  Update-Tools
```

**Bulk Operations:**
```powershell
# Power on all VMs in folder
Get-Folder "Training" | `
  Get-VM | `
  Start-VM

# Snapshot all VMs
Get-VM | % {
  New-Snapshot -VM $_ `
    -Name "Scheduled" `
    -Description (Get-Date)
}

# Report VM resources
Get-VM | Select Name, `
  NumCPU, `
  MemoryGB, `
  @{N="DiskGB";E={[math]::Round((Get-HardDisk -VM $_).CapacityGB)}} | `
  Export-CSV vms.csv
```

---

**Изготвил:** [Име на учителя]  
**Дата на изготвяне:** Декември 2024 г.
