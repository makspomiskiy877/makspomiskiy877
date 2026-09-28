# About-Me

Привет! 👋

Я Максим, начинающий специалист по информационной безопасности.

🛡️ Навыки
Linux: Kali Linux, Ubuntu
Основы компьютерных сетей и сетевых протоколов
Nmap — сканирование сети и обнаружение сервисов
Wireshark — анализ сетевого трафика
OWASP ZAP — тестирование веб-приложений
Nikto — поиск проблем конфигурации веб-серверов
Основы OSINT
Основы тестирования веб-приложений на уязвимости
Работа с виртуальными машинами VirtualBox
🔬 Практические работы
Анализ сети

Сканирование лабораторной сети с помощью Nmap и анализ обнаруженных портов и сервисов.

Анализ трафика

Перехват и исследование сетевого трафика в Wireshark.

Тестирование веб-приложений

Практика поиска уязвимостей в учебных лабораторных средах с использованием OWASP ZAP, Nikto и ручного тестирования.

OSINT

Практика поиска и анализа информации из открытых источников.

🧰 Инструменты

Nmap Wireshark OWASP ZAP Nikto Kali Linux Ubuntu VirtualBox

📜 Образование и сертификаты

[Основы информационной безопасности](https://github.com/makspomiskiy877/makspomiskiy877/blob/main/certificate.pdf)

[Сети передачи данных и безопасность](https://github.com/makspomiskiy877/makspomiskiy877/blob/main/Data%20Transmission%20Networks%20and.pdf)

[Git — система контроля версий IB](https://github.com/makspomiskiy877/makspomiskiy877/blob/main/Git%20%E2%80%94%20IB%20version%20control%20system.pdf)

[Безопасность операционных систем, системное программирование](https://github.com/makspomiskiy877/makspomiskiy877/blob/main/Operating%20system%20security.pdf)

[Современная разработка ПО](https://github.com/makspomiskiy877/makspomiskiy877/blob/main/Modern%20Software%20Development.pdf)

[Администрирование СЗИ](https://github.com/makspomiskiy877/makspomiskiy877/blob/main/Administration%20of%20Information%20Security%20Tools.pdf)

[Современная киберпреступность и методы противодействия](https://github.com/makspomiskiy877/makspomiskiy877/blob/main/Modern%20Cybercrime%20and%20Countermeasures.pdf)

[Реагирование на инциденты ИБ и проактивный поиск угроз](https://github.com/makspomiskiy877/makspomiskiy877/blob/main/Information%20Security%20Incident%20Response%20and%20Proactive%20Threat%20Hunting.pdf)

[Аttack & Defence](https://github.com/makspomiskiy877/makspomiskiy877/blob/main/%D0%90ttack%20%26%20Defence.pdf)

[Свидетельство](https://github.com/makspomiskiy877/makspomiskiy877/blob/main/Certificateend.pdf)

[Диплом](https://github.com/makspomiskiy877/makspomiskiy877/blob/main/66891_dpp_2.pdf)




📂 Портфолио

Track Penetration Testing (Дипломная работа)

Цель: Провести разведку инфраструктуры, определить доступные сервисы, исследовать веб-приложение и найти потенциальные уязвимости.

Инструменты: Kali Linux Nmap Gobuster WHOIS Shodan Linux CLI ручное тестирование веб-приложения

Этап 1 — OSINT

С помощью WHOIS, Reverse DNS и Shodan была собрана информация о сервере.

Удалось определить:

хостинг — TimeWeb;

ASN — AS9123;

SSH — OpenSSH 8.2p1;

открытые порты — 22 и 7788.

Этап 2 — Сканирование

Для определения сервиса использовался Nmap:

nmap -Pn -sV -sC -p 7788 <TARGET_IP>

На 7788/tcp обнаружено веб-приложение на Tornado 5.1.1.

С помощью Gobuster были найдены:

/index.html
/read
/search
/upload

Этап 3 — Тестирование

Проверены основные функции приложения:

авторизация;

поиск;

Server Status;

загрузка файлов;

чтение файлов.

Найденные уязвимости

1. Небезопасная загрузка файлов

Приложение принимало файлы .php.

Риск: потенциальная возможность выполнения загруженного кода. Выполнение PHP в ходе тестирования не подтвердилось.

2. Information Disclosure — Medium

Приложение раскрывало Python traceback и внутренние пути сервера.

Обнаружена информация об использовании Python 2.7 и Tornado.

3. Reflected XSS — Medium

В параметре поиска подтверждена XSS.

/search?q='><script>alert(1)</script>

В браузере успешно выполнялся alert(1).

4. Path Traversal / LFI — High

Обнаружена возможность чтения файлов:

/read?file=../server.py

Удалось получить исходный код server.py.

5. Раскрытие учётных данных — High

Анализ server.py позволил обнаружить действительные административные учётные данные.

После авторизации приложение вернуло:

Login Success, Hello admin

Цепочка атаки

Gobuster
   ↓
/read
   ↓
Path Traversal
   ↓
server.py
   ↓
Учётные данные
   ↓
Доступ администратора

 Рекомендации

устранить Path Traversal;

экранировать пользовательский ввод для защиты от XSS;

ограничить типы загружаемых файлов;

отключить отображение traceback;

не хранить пароли в исходном коде;

использовать bcrypt / Argon2 / PBKDF2;

обновить устаревшие компоненты.

 Полученные навыки

OSINT • Nmap • Gobuster • Web Pentesting • XSS • Path Traversal / LFI • File Upload Testing • Linux • Vulnerability Assessment

Проект выполнен исключительно в учебных целях на разрешённой инфраструктуре.








