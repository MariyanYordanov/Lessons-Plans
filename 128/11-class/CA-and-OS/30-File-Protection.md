# УРОЧЕН ПЛАН №30
## УЧЕБНА ПРАКТИКА: КОМПЮТЪРНИ АРХИТЕКТУРИ И ОПЕРАЦИОННИ СИСТЕМИ
### XI КЛАС

---

## 1. ОСНОВНИ ДАННИ

- **Училище:** 128-мо СУ "Алберт Айнщайн", гр.София
- **Клас:** XI клас
- **Учител:** Мариян Йорданов
- **Предмет:** Учебна практика: Компютърни архитектури и операционни системи
- **Тема на урока:** Защита на файлове и права за достъп
- **Дата:** ____________
- **Продължителност:** 90 минути
- **Тип урок:** Нови знания

---

## 2. ЦЕЛИ И ЗАДАЧИ

### ОБРАЗОВАТЕЛНИ ЦЕЛИ:
1. Да разберат концепцията за файлова защита в ОС
2. Да познават модели за контрол на достъпа (DAC, MAC, RBAC)
3. Да могат да прилагат ACL в Linux и Windows
4. Да разбират важността на правата за сигурността

---

## 5. ХОД НА УРОКА

### **НОВ МАТЕРИАЛ (40 минути)**

#### **Модели за контрол на достъпа:**

```
DAC (Discretionary Access Control):
├── Собственикът определя правата
├── Гъвкав, но по-малко сигурен
├── Използван в: Linux (chmod), Windows (NTFS)
└── Пример: chmod 750 file.txt

MAC (Mandatory Access Control):
├── Системата определя правата (labels)
├── По-сигурен, по-строг
├── Използван в: SELinux, AppArmor
└── Пример: Класификации (Top Secret, Secret...)

RBAC (Role-Based Access Control):
├── Права базирани на роли
├── Потребител → Роля → Права
├── Използван в: Active Directory, databases
└── Пример: Admin role, User role, Guest role
```

#### **ACL (Access Control Lists):**

**Linux ACL:**
```bash
# Преглед на ACL
getfacl file.txt

# Задаване на ACL
setfacl -m u:username:rwx file.txt    # За потребител
setfacl -m g:groupname:rx file.txt    # За група
setfacl -m o::r file.txt              # За други

# Премахване
setfacl -x u:username file.txt

# Рекурсивно
setfacl -R -m u:user:rx directory/

# Default ACL (за нови файлове в директория)
setfacl -d -m u:user:rwx directory/
```

**Windows NTFS права:**
```
Основни права:
├── Full Control - всичко
├── Modify - промяна и изтриване
├── Read & Execute - четене и изпълнение
├── List Folder Contents - списък (за папки)
├── Read - само четене
└── Write - само писане

Разширени права:
├── Traverse folder / execute file
├── List folder / read data
├── Read attributes
├── Read extended attributes
├── Create files / write data
├── Create folders / append data
├── Write attributes
├── Write extended attributes
├── Delete subfolders and files
├── Delete
├── Read permissions
├── Change permissions
└── Take ownership

GUI: Right-click → Properties → Security
CMD: icacls filename
PowerShell: Get-Acl filename
```

#### **Наследяване на права:**

```
Windows:
┌─────────────┐
│  Folder A   │ ← Права: Users=Read
└──────┬──────┘
       │ (наследяване)
       ▼
┌─────────────┐
│  Folder B   │ ← Наследява: Users=Read
└──────┬──────┘
       │
       ▼
┌─────────────┐
│   File.txt  │ ← Наследява: Users=Read
└─────────────┘

Прекъсване на наследяване:
Properties → Security → Advanced → 
Disable inheritance
```

---

### **ПРАКТИЧЕСКА РАБОТА (30 минути)**

**Задача 1: Linux ACL**
```bash
# Създайте файл
touch secret.txt
echo "Confidential data" > secret.txt

# Базови права
chmod 600 secret.txt
ls -l secret.txt

# Добавете ACL за друг потребител
sudo setfacl -m u:testuser:r secret.txt
getfacl secret.txt

# Премахнете ACL
setfacl -b secret.txt
```

**Задача 2: Windows права**
```powershell
# Преглед на права
icacls C:\test\file.txt

# Добавяне на права
icacls C:\test\file.txt /grant Users:R

# Премахване
icacls C:\test\file.txt /remove Users

# PowerShell
Get-Acl C:\test\file.txt | Format-List
```

---

### **ОБОБЩЕНИЕ**

```
КЛЮЧОВИ ТОЧКИ:

1. DAC - собственикът контролира достъпа
2. MAC - системата контролира (SELinux)
3. RBAC - базирано на роли
4. ACL разширяват базовите права (rwx)
5. Windows има богата ACL система (NTFS)
6. Наследяването опростява управлението
```

---

### **ДОМАШНА РАБОТА**

1. Какво е разликата между DAC и MAC?
2. Създайте файл с ACL, който дава различни права на 2 потребителя
3. Изследвайте какво е SELinux

---

**Изготвил:** Мариян Йорданов  
**Дата на изготвяне:** Януари 2025 г.
