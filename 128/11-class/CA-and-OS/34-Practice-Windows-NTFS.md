# УРОЧЕН ПЛАН №34
## УЧЕБНА ПРАКТИКА: КОМПЮТЪРНИ АРХИТЕКТУРИ И ОПЕРАЦИОННИ СИСТЕМИ
### XI КЛАС

---

## 1. ОСНОВНИ ДАННИ

- **Училище:** 128-мо СУ "Алберт Айнщайн", гр.София
- **Клас:** XI клас
- **Учител:** Мариян Йорданов
- **Предмет:** Учебна практика: Компютърни архитектури и операционни системи
- **Тема на урока:** Практическа работа с Windows NTFS/FAT32
- **Дата:** ____________
- **Продължителност:** 90 минути
- **Тип урок:** Упражнение

---

## 2. ЦЕЛИ И ЗАДАЧИ

### ОБРАЗОВАТЕЛНИ ЦЕЛИ:
1. Да придобият практически умения за работа с NTFS
2. Да могат да конвертират между файлови системи
3. Да използват NTFS функции (compression, encryption)
4. Да управляват права и атрибути

---

## 5. ХОД НА УРОКА

### **ТЕОРЕТИЧНА ЧАСТ (20 минути)**

#### **NTFS специални функции:**

```
COMPRESSION (Компресия):
├── Прозрачна за приложенията
├── По файл или по папка
├── Спестява място, но използва CPU
└── Не препоръчително за: игри, видео, бази данни

Активиране:
Properties → General → Advanced → 
"Compress contents to save disk space"

CLI: compact /c filename
     compact /u filename (decompress)

ENCRYPTION (EFS - Encrypting File System):
├── Криптира данните на диска
├── Прозрачно за потребителя
├── Базирано на сертификати
├── ВАЖНО: Backup на сертификата!
└── Не работи с compression едновременно

Активиране:
Properties → General → Advanced →
"Encrypt contents to secure data"

CLI: cipher /e filename
     cipher /d filename (decrypt)

ALTERNATE DATA STREAMS (ADS):
├── Скрити данни, прикрепени към файл
├── Използвани от Windows за metadata
├── Могат да се използват злонамерено
└── Не се виждат в Explorer

Пример:
echo "hidden" > file.txt:secret
more < file.txt:secret
dir /r    # показва ADS
```

#### **FAT32 vs NTFS:**

```
Кога FAT32:
├── USB флашки за съвместимост
├── SD карти за камери
├── Boot дялове (някои)
└── Споделяне между OS

Кога NTFS:
├── Системен дял (Windows)
├── Файлове > 4 GB
├── Нужда от права за достъп
├── Encryption/Compression
└── Големи дискове
```

---

### **ПРАКТИЧЕСКА РАБОТА (55 минути)**

**Задача 1: Работа с права (15 мин)**
```powershell
# Създайте тестова папка
mkdir C:\TestNTFS
cd C:\TestNTFS

# Прегледайте текущите права
icacls .

# Създайте файл
echo "Test content" > test.txt

# Добавете права за конкретен потребител
icacls test.txt /grant Users:R

# Премахнете наследяване и задайте изрични права
icacls test.txt /inheritance:r
icacls test.txt /grant:r Administrators:F

# Проверете
icacls test.txt
```

**Задача 2: Compression (10 мин)**
```cmd
# Създайте голям файл
fsutil file createnew bigfile.txt 104857600

# Проверете размера
dir bigfile.txt

# Компресирайте
compact /c bigfile.txt

# Проверете новия размер
compact /s bigfile.txt
dir bigfile.txt

# Декомпресирайте
compact /u bigfile.txt
```

**Задача 3: Alternate Data Streams (10 мин)**
```cmd
# Създайте файл с ADS
echo "Main content" > normal.txt
echo "Hidden content" > normal.txt:hidden

# Прочетете ADS
more < normal.txt:hidden

# Покажете ADS
dir /r

# PowerShell преглед
Get-Item normal.txt -Stream *
```

**Задача 4: Конвертиране FAT32 → NTFS (10 мин)**
```cmd
# ВНИМАНИЕ: Само с тестов USB/дял!
# Проверете файловата система
fsutil fsinfo volumeinfo E:

# Конвертиране (необратимо без форматиране)
convert E: /fs:ntfs

# Форматиране (изтрива данните!)
format E: /fs:ntfs /q
format E: /fs:fat32 /q
```

**Задача 5: Disk cleanup и анализ (10 мин)**
```powershell
# Анализ на използване
Get-ChildItem C:\ -Recurse -ErrorAction SilentlyContinue |
    Group-Object Extension |
    Sort-Object Count -Descending |
    Select-Object Name, Count -First 10

# Големи файлове
Get-ChildItem C:\Users -Recurse -ErrorAction SilentlyContinue |
    Where-Object {$_.Length -gt 100MB} |
    Sort-Object Length -Descending |
    Select-Object FullName, @{N='SizeMB';E={[math]::Round($_.Length/1MB,2)}}
```

---

### **ОБОБЩЕНИЕ (10 минути)**

```
КЛЮЧОВИ ТОЧКИ:

1. NTFS поддържа compression и encryption
2. icacls управлява NTFS права от CLI
3. ADS могат да съдържат скрити данни
4. FAT32 → NTFS конвертиране е възможно без загуба
5. NTFS → FAT32 изисква форматиране
6. Compression ≠ Encryption (различни функции)
```

---

### **ДОМАШНА РАБОТА**

1. Компресирайте папка на вашия компютър и измерете спестеното място
2. Проверете дали имате файлове с ADS
3. Каква файлова система е на вашия USB флаш?

---

**Изготвил:** Мариян Йорданов  
**Дата на изготвяне:** Януари 2025 г.
