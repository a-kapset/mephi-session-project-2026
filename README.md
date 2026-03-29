# Сессионный проект по дисциплине "Операционные системы семейства Unix" (МИФИ 2026)

**Студент:** Артём Капсет

**Зачётная книжка:** М255580

**Курс:** Операционные системы семейства Unix

**Среда:** Fedora 43 Server, VirtualBox

---

## Что сделано

### 1. Управление сетью
- Статический IP `192.168.1.100/24` на интерфейсе `enp0s8` (Host-Only)
- Шлюз `192.168.1.1`, DNS `8.8.8.8`
- Hostname: `mephi-2026.domain.local`
- Проверка связности: ping до `192.168.1.1` и `8.8.8.8`

### 2. Управление ПО
- Установлены пакеты: `nginx`, `tcpdump`, `libcap-ng-utils`
- RPM-пакет `tcpdump` скачан через `dnf download` и установлен через `rpm`

### 3. Файловые системы и сервисы
- Раздел `/dev/sdb1` с ext4, метка `MEPHI_DATA`
- Автомонтирование в `/data/mephi-web` через `/etc/fstab`
- nginx запущен и включён в автозапуск

### 4. Управление доступом
- Пользователь `mephi-admin`, группа `mephi-devs`
- Права `2775` (setgid) на `/data/mephi-web`
- SELinux Enforcing, контекст `httpd_sys_content_t`
- Capabilities `cap_net_raw,cap_net_admin+ep` на `tcpdump`

### 5. Аутентификация и тестирование
- Вход root заблокирован через PAM (`pam_listfile.so`)
- `curl http://localhost` и `curl http://192.168.1.100` возвращают `Hello from Student: М255580`

## Артефакты

| Файл | Раздел | Описание |
|------|--------|----------|
| `project_history.txt` | Все | История команд |
| `network_check.txt` | 1.2 | Результаты ping |
| `nginx_recent_logs.txt` | 3.2 | Логи nginx |
| `fstab.txt` | 3.1 | Автомонтирование |
| `selinux_status.txt` | 4.2 | Режим SELinux |
| `file_contexts.txt` | 4.2 | Контекст SELinux |
| `tcpdump_capabilities.txt` | 4.2 | Capabilities |
| `permissions.txt` | 4.1 | Права и владелец |
| `users_groups.txt` | 4.1 | Пользователи и группы |
| `index.html` | 5.2 | Web-страница |
| `curl_output.txt` | 5.2 | Результат curl |
| `mephi-nginx-screenshot.png` | 5.2 | Скриншот nginx |
| `tcpdump.rpm` | 2.2 | RPM-пакет |
| `check-after-reboot/` | — | Скриншоты проверки после перезагрузки |
