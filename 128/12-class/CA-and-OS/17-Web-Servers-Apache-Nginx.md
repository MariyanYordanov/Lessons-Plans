# УРОЧЕН ПЛАН №17
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
| **Тема на урока:** | Web сървъри - Apache и Nginx конфигурация |
| **Дата:** | ____________ |
| **Час:** | ____________ |
| **Продължителност:** | 90 минути (2 учебни часа) |
| **Тип урок:** | Упражнение |
| **Място на провеждане:** | Компютърен кабинет |

---

## 2. ЦЕЛИ И ЗАДАЧИ

### ОБРАЗОВАТЕЛНИ ЦЕЛИ:
1. Учениците да разбират ролята на web сървърите в интернет инфраструктурата
2. Да инсталират и конфигурират Apache HTTP Server
3. Да инсталират и конфигурират Nginx
4. Да създават виртуални хостове (Virtual Hosts)
5. Да разбират разликата между Apache и Nginx архитектура

### ВЪЗПИТАТЕЛНИ ЦЕЛИ:
1. Формиране на разбиране за сигурност на web приложенията
2. Развиване на професионален подход към конфигурация на услуги
3. Изграждане на отговорност при публикуване на web съдържание
4. Насърчаване на документиране на конфигурации

### РАЗВИВАЩИ ЦЕЛИ:
1. Развитие на практически умения за web администрация
2. Усъвършенстване на troubleshooting способности
3. Формиране на умения за сравнителен анализ
4. Развитие на логическо мислене при конфигурация

---

## 3. СЪДЪРЖАНИЕ

### ОСНОВНИ ЗНАНИЯ:

**Теоретични концепции:**
- HTTP протокол - заявки и отговори
- Web сървър архитектура
- Apache MPM (Multi-Processing Modules)
- Nginx event-driven модел
- Virtual Hosts концепция
- SSL/TLS основи

**Технически детайли:**
- Apache конфигурационни файлове
- Nginx конфигурационна структура
- DocumentRoot и директиви
- Модули и разширения

### ОСНОВНИ УМЕНИЯ:
- Инсталация на Apache и Nginx
- Конфигуриране на виртуални хостове
- Управление на услугите чрез systemctl
- Базова SSL конфигурация
- Четене и анализ на логове

### МЕЖДУПРЕДМЕТНИ ВРЪЗКИ:
1. **Мрежови технологии** - HTTP/HTTPS, DNS, портове
2. **Програмиране** - HTML, PHP интеграция
3. **Информационна сигурност** - SSL сертификати, защита
4. **Бази данни** - LAMP/LEMP stack

---

## 4. МЕТОДИ И СРЕДСТВА

### МЕТОДИ НА ПРЕПОДАВАНЕ:
1. Демонстрация с обяснение
2. Практически упражнения стъпка по стъпка
3. Сравнителен анализ на двата сървъра
4. Самостоятелна работа
5. Troubleshooting на проблеми

### УЧЕБНИ СРЕДСТВА И МАТЕРИАЛИ:
- Компютри с Ubuntu 24.04 LTS
- Терминален достъп с sudo права
- Браузър за тестване
- Справочник с команди (Приложение 1)
- Конфигурационни шаблони (Приложение 2)

---

## 5. ХОД НА УРОКА

### **1. ОРГАНИЗАЦИОНЕН МОМЕНТ (5 минути)**

**Въведение:**
- Проверка на присъстващите
- Стартиране на Ubuntu VM
- Представяне на целите

**Мотивиращ въпрос:**
"Когато отворите уеб страница, какво се случва зад кулисите? Кой софтуер обслужва вашата заявка?"

---

### **2. АКТУАЛИЗАЦИЯ (8 минути)**

**Преговор на HTTP:**
```
HTTP Request-Response цикъл:

Клиент (браузър)              Web сървър
     │                             │
     │──── GET /index.html ───────>│
     │                             │
     │<─── HTTP 200 OK ────────────│
     │     + HTML съдържание       │

Статус кодове:
• 200 OK - Успешна заявка
• 301/302 - Пренасочване
• 403 Forbidden - Забранен достъп
• 404 Not Found - Не е намерен
• 500 Internal Server Error - Сървърна грешка
```

**Въпроси:**
1. На кой порт работи HTTP? (80)
2. На кой порт работи HTTPS? (443)
3. Какво е DNS и как е свързано с web сървърите?

---

### **3. НОВ МАТЕРИАЛ И ПРАКТИКА (55 минути)**

#### **Част 1: Въведение в Apache и Nginx (10 минути)**

**Сравнение:**
```
┌─────────────────────────────────────────────────────────────┐
│                    APACHE vs NGINX                          │
├─────────────────────────────────────────────────────────────┤
│ Apache HTTP Server              │ Nginx                     │
│ • Създаден 1995                 │ • Създаден 2004           │
│ • Process/Thread модел          │ • Event-driven модел      │
│ • .htaccess поддръжка           │ • Няма .htaccess          │
│ • По-гъвкав за динамично        │ • По-бърз за статично     │
│   съдържание                    │   съдържание              │
│ • Повече памет на connection    │ • По-малко памет          │
│ • ~31% от web сървърите         │ • ~34% от web сървърите   │
└─────────────────────────────────────────────────────────────┘

Кога да използвате кой:
• Apache: Shared hosting, .htaccess нужен, mod_rewrite
• Nginx: Reverse proxy, load balancing, висок трафик
• Комбинация: Nginx пред Apache (най-добро от двата)
```

---

#### **Част 2: Инсталация и конфигурация на Apache (20 минути)**

**Практика 2.1: Инсталация на Apache**
```bash
# Актуализация на пакетите
sudo apt update

# Инсталация на Apache
sudo apt install apache2 -y

# Проверка на статуса
sudo systemctl status apache2

# Тестване в браузър
# Отворете: http://localhost или http://[IP_ADDRESS]
# Трябва да видите Apache2 Ubuntu Default Page
```

**Практика 2.2: Структура на директориите**
```bash
# Apache директории в Ubuntu
/etc/apache2/                    # Конфигурационна директория
├── apache2.conf                 # Главен конфигурационен файл
├── ports.conf                   # Портове (Listen 80, 443)
├── sites-available/             # Налични сайтове
│   └── 000-default.conf         # Подразбиращ се сайт
├── sites-enabled/               # Активни сайтове (symlinks)
├── mods-available/              # Налични модули
├── mods-enabled/                # Активни модули
└── conf-available/              # Допълнителни конфигурации

/var/www/html/                   # DocumentRoot (web файлове)
/var/log/apache2/                # Логове
├── access.log                   # Достъп
└── error.log                    # Грешки
```

**Практика 2.3: Основни команди**
```bash
# Управление на услугата
sudo systemctl start apache2
sudo systemctl stop apache2
sudo systemctl restart apache2
sudo systemctl reload apache2    # Презареждане без прекъсване

# Активиране/деактивиране на автоматичен старт
sudo systemctl enable apache2
sudo systemctl disable apache2

# Проверка на конфигурацията
sudo apache2ctl configtest
# Syntax OK = всичко е наред

# Активиране/деактивиране на сайтове
sudo a2ensite sitename.conf
sudo a2dissite sitename.conf

# Активиране/деактивиране на модули
sudo a2enmod rewrite
sudo a2dismod rewrite
```

**Практика 2.4: Създаване на Virtual Host**
```bash
# 1. Създаване на директория за сайта
sudo mkdir -p /var/www/mysite.local/html
sudo chown -R $USER:$USER /var/www/mysite.local

# 2. Създаване на тестова страница
cat << 'EOF' | sudo tee /var/www/mysite.local/html/index.html
<!DOCTYPE html>
<html lang="bg">
<head>
    <meta charset="UTF-8">
    <title>Моят сайт</title>
</head>
<body>
    <h1>Добре дошли в mysite.local!</h1>
    <p>Apache Virtual Host работи успешно.</p>
    <p>Сървърно време: <?php echo date('Y-m-d H:i:s'); ?></p>
</body>
</html>
EOF

# 3. Създаване на Virtual Host конфигурация
sudo nano /etc/apache2/sites-available/mysite.local.conf
```

**Съдържание на mysite.local.conf:**
```apache
<VirtualHost *:80>
    ServerAdmin admin@mysite.local
    ServerName mysite.local
    ServerAlias www.mysite.local
    DocumentRoot /var/www/mysite.local/html
    
    <Directory /var/www/mysite.local/html>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
    
    ErrorLog ${APACHE_LOG_DIR}/mysite_error.log
    CustomLog ${APACHE_LOG_DIR}/mysite_access.log combined
</VirtualHost>
```

```bash
# 4. Активиране на сайта
sudo a2ensite mysite.local.conf

# 5. Добавяне в /etc/hosts
echo "127.0.0.1 mysite.local www.mysite.local" | sudo tee -a /etc/hosts

# 6. Презареждане на Apache
sudo systemctl reload apache2

# 7. Тестване
curl http://mysite.local
# или в браузър: http://mysite.local
```

---

#### **Част 3: Инсталация и конфигурация на Nginx (20 минути)**

**Практика 3.1: Спиране на Apache и инсталация на Nginx**
```bash
# Спиране на Apache (заема порт 80)
sudo systemctl stop apache2
sudo systemctl disable apache2

# Инсталация на Nginx
sudo apt install nginx -y

# Стартиране и проверка
sudo systemctl start nginx
sudo systemctl status nginx

# Тестване в браузър
# http://localhost - Nginx welcome page
```

**Практика 3.2: Структура на Nginx**
```bash
# Nginx директории
/etc/nginx/                      # Конфигурационна директория
├── nginx.conf                   # Главен конфигурационен файл
├── sites-available/             # Налични сайтове
│   └── default                  # Подразбиращ се сайт
├── sites-enabled/               # Активни сайтове (symlinks)
├── conf.d/                      # Допълнителни конфигурации
└── snippets/                    # Преизползваеми snippets

/var/www/html/                   # DocumentRoot
/var/log/nginx/                  # Логове
├── access.log
└── error.log
```

**Практика 3.3: Основни команди за Nginx**
```bash
# Управление на услугата
sudo systemctl start nginx
sudo systemctl stop nginx
sudo systemctl restart nginx
sudo systemctl reload nginx

# Проверка на конфигурацията
sudo nginx -t
# nginx: configuration file /etc/nginx/nginx.conf syntax is ok
# nginx: configuration file /etc/nginx/nginx.conf test is successful

# Преглед на nginx.conf
sudo cat /etc/nginx/nginx.conf
```

**Практика 3.4: Създаване на Nginx Server Block**
```bash
# 1. Създаване на директория (ако не съществува)
sudo mkdir -p /var/www/nginxsite.local/html
sudo chown -R $USER:$USER /var/www/nginxsite.local

# 2. Създаване на тестова страница
cat << 'EOF' | sudo tee /var/www/nginxsite.local/html/index.html
<!DOCTYPE html>
<html lang="bg">
<head>
    <meta charset="UTF-8">
    <title>Nginx Сайт</title>
    <style>
        body { font-family: Arial; text-align: center; padding: 50px; }
        h1 { color: #009639; }
    </style>
</head>
<body>
    <h1>Добре дошли в nginxsite.local!</h1>
    <p>Nginx Server Block работи успешно.</p>
</body>
</html>
EOF

# 3. Създаване на Server Block конфигурация
sudo nano /etc/nginx/sites-available/nginxsite.local
```

**Съдържание на nginxsite.local:**
```nginx
server {
    listen 80;
    listen [::]:80;
    
    server_name nginxsite.local www.nginxsite.local;
    root /var/www/nginxsite.local/html;
    index index.html index.htm;
    
    location / {
        try_files $uri $uri/ =404;
    }
    
    # Статични файлове с кеширане
    location ~* \.(jpg|jpeg|png|gif|ico|css|js)$ {
        expires 30d;
        add_header Cache-Control "public, immutable";
    }
    
    # Логове
    access_log /var/log/nginx/nginxsite_access.log;
    error_log /var/log/nginx/nginxsite_error.log;
}
```

```bash
# 4. Активиране на сайта
sudo ln -s /etc/nginx/sites-available/nginxsite.local /etc/nginx/sites-enabled/

# 5. Добавяне в /etc/hosts
echo "127.0.0.1 nginxsite.local www.nginxsite.local" | sudo tee -a /etc/hosts

# 6. Проверка и презареждане
sudo nginx -t
sudo systemctl reload nginx

# 7. Тестване
curl http://nginxsite.local
```

---

#### **Част 4: Nginx като Reverse Proxy (5 минути)**

**Концепция:**
```
Клиент ──> Nginx (Reverse Proxy) ──> Apache/Node.js/Python
              │
              └── SSL терминация
              └── Кеширане
              └── Load balancing
```

**Примерна конфигурация:**
```nginx
# /etc/nginx/sites-available/proxy-example
server {
    listen 80;
    server_name app.local;
    
    location / {
        proxy_pass http://127.0.0.1:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_cache_bypass $http_upgrade;
    }
}
```

---

### **4. ЗАТВЪРЖДАВАНЕ (12 минути)**

**Практическа задача:**
```
СЦЕНАРИЙ: Създайте среда с два сайта

1. Стартирайте Nginx
2. Създайте два сайта:
   - site1.local с червен фон
   - site2.local със син фон
3. И двата сайта да работят на порт 80
4. Тествайте достъпа до двата сайта

БОНУС: Добавете лого изображение и го кеширайте за 7 дни
```

**Проверка на резултатите:**
```bash
# Проверка на конфигурацията
sudo nginx -t

# Проверка на активни сайтове
ls -la /etc/nginx/sites-enabled/

# Тестване
curl -I http://site1.local
curl -I http://site2.local

# Преглед на логове
sudo tail -f /var/log/nginx/access.log
```

---

### **5. ОБОБЩЕНИЕ (8 минути)**

**Ключови концепции:**
```
Apache:
✓ Process/Thread базиран
✓ .htaccess поддръжка
✓ a2ensite/a2dissite за управление на сайтове
✓ apache2ctl configtest за проверка

Nginx:
✓ Event-driven архитектура
✓ По-ефективен за статично съдържание
✓ Symlinks за активиране на сайтове
✓ nginx -t за проверка
✓ Отличен reverse proxy

Общо:
✓ Virtual Hosts = множество сайтове на един сървър
✓ DocumentRoot = директория с web файлове
✓ /etc/hosts за локално тестване
```

---

### **6. ДОМАШНА РАБОТА (2 минути)**

**Задание:**
```
1. Инсталирайте и конфигурирайте LEMP stack:
   - Linux (вече имате)
   - Nginx
   - MySQL (sudo apt install mysql-server)
   - PHP (sudo apt install php-fpm php-mysql)

2. Създайте PHP страница, която показва phpinfo()

3. Проучете: Как да добавите безплатен SSL 
   сертификат с Let's Encrypt?

Очаквано време: 45-60 минути
```

---

## 6. ОЦЕНЯВАНЕ

### КРИТЕРИИ ЗА ОЦЕНЯВАНЕ:

| Компонент | Точки | Процент |
|-----------|-------|---------|
| Инсталация на Apache/Nginx | 10 | 20% |
| Създаване на Virtual Host | 15 | 25% |
| Конфигуриране на Nginx | 15 | 25% |
| Практическа задача | 10 | 20% |
| Домашна работа | 5 | 10% |
| **ОБЩО** | **55** | **100%** |

---

## 8. ПРИЛОЖЕНИЯ

### ПРИЛОЖЕНИЕ 1: СПРАВОЧНИК С КОМАНДИ

```
╔══════════════════════════════════════════════════════════════╗
║                 WEB СЪРВЪРИ - КОМАНДИ                        ║
╚══════════════════════════════════════════════════════════════╝

APACHE
───────────────────────────────────────────────────────────────
# Инсталация
sudo apt install apache2

# Управление
sudo systemctl start|stop|restart|reload apache2
sudo systemctl enable|disable apache2

# Конфигурация
sudo apache2ctl configtest         # Проверка
sudo a2ensite sitename.conf        # Активиране на сайт
sudo a2dissite sitename.conf       # Деактивиране
sudo a2enmod modname               # Активиране на модул
sudo a2dismod modname              # Деактивиране

# Логове
sudo tail -f /var/log/apache2/access.log
sudo tail -f /var/log/apache2/error.log

NGINX
───────────────────────────────────────────────────────────────
# Инсталация
sudo apt install nginx

# Управление
sudo systemctl start|stop|restart|reload nginx

# Конфигурация
sudo nginx -t                      # Проверка
sudo nginx -T                      # Покажи цялата конфигурация

# Активиране на сайт
sudo ln -s /etc/nginx/sites-available/site /etc/nginx/sites-enabled/

# Деактивиране
sudo rm /etc/nginx/sites-enabled/site

# Логове
sudo tail -f /var/log/nginx/access.log
sudo tail -f /var/log/nginx/error.log

═══════════════════════════════════════════════════════════════
```

### ПРИЛОЖЕНИЕ 2: КОНФИГУРАЦИОННИ ШАБЛОНИ

**Apache Virtual Host:**
```apache
<VirtualHost *:80>
    ServerAdmin webmaster@example.com
    ServerName example.com
    ServerAlias www.example.com
    DocumentRoot /var/www/example.com/html
    
    <Directory /var/www/example.com/html>
        Options -Indexes +FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
    
    ErrorLog ${APACHE_LOG_DIR}/example_error.log
    CustomLog ${APACHE_LOG_DIR}/example_access.log combined
</VirtualHost>
```

**Nginx Server Block:**
```nginx
server {
    listen 80;
    listen [::]:80;
    
    server_name example.com www.example.com;
    root /var/www/example.com/html;
    index index.html index.htm index.php;
    
    location / {
        try_files $uri $uri/ =404;
    }
    
    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php8.3-fpm.sock;
    }
    
    location ~ /\.ht {
        deny all;
    }
    
    access_log /var/log/nginx/example_access.log;
    error_log /var/log/nginx/example_error.log;
}
```

---

*Документът е създаден за учебната 2025/2026 година*
*Съответства на изискванията на МОН за професионална подготовка*
*Специалност: Икономическо информационно осигуряване (код 482021)*
