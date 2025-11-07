# Ansible Role: OpenVPN Installation via angristan/openvpn-install

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

---

# ENG

---

This role automates the deployment of an **OpenVPN server** on Linux hosts using the well-established [`angristan/openvpn-install`](https://github.com/angristan/openvpn-install) script.  
It’s ideal for quickly and securely setting up your own VPN server—whether in the cloud, on a VPS, or on a local machine.

> 💡 **Important**: This role is intended **only for fresh installations** or infrastructure fully managed by Ansible. Do **not** apply it to manually configured OpenVPN servers unless you fully understand the implications.

---

## 📦 Supported Operating Systems

The role inherits OS support from the upstream script:

- **Debian** 12+
- **Ubuntu** 22.04+

> 🔧 Requires `systemd` and an enabled TUN kernel module.

*(Note: The original script also supports Fedora, CentOS, AlmaLinux, Rocky Linux, Oracle Linux, Arch, and Amazon Linux—but this Ansible role currently focuses on Debian/Ubuntu.)*

---

## 🚀 Features

- Fully automated OpenVPN installation and configuration  
- Generation of client `.ovpn` configuration files  
- Support for unattended (headless) mode  
- Idempotent: safe to run repeatedly  
- Client management: add new users on demand  
- Secure defaults out of the box: (AES-128-GCM, TLS 1.2+, tls-crypt ...)

---

## ⚙️ Variables

Key customizable parameters (define in `vars`, `group_vars`, or when invoking the role):

| Variable               | Default                     | Description |
|------------------------|-----------------------------|-------------|
| `openvpn_clients`      | `["client1"]`               | List of client names for which `.ovpn` configs will be generated |
| `openvpn_script_path`  | `/root/openvpn-install.sh`  | Path on the target host where the installer script is saved |
| `openvpn_download_url` | `https://raw.githubusercontent.com/angristan/openvpn-install/master/openvpn-install.sh` | Source URL to download the script |
| `openvpn_port`         | `1195`                      | OpenVPN server port |
| `openvpn_recreate`     | `false`                     | If `true`, forces regeneration of client configs (use with caution) |
| `nginx_port`           | 80                  | Nginx operating port |

**Example usage:**

```yaml
openvpn_clients:
  - laptop
  - phone
  - tablet
openvpn_recreate: true
```
## ✅ Access

After the role is launched for the first time, the file with access data for the filebrowser panel is located in the home directory of the user who initiated the installation process.

---

---
# RUS
---
Эта роль автоматизирует развертывание **OpenVPN-сервера** на Linux-хостах с использованием проверенного скрипта [`angristan/openvpn-install`](https://github.com/angristan/openvpn-install).  
Подходит для быстрого и безопасного запуска собственного VPN-сервера в облаке, на VPS или локальном сервере.

> 💡 **Важно**: Роль предназначена **только для новых установок** или управляемых через Ansible инфраструктур. Не рекомендуется применять к уже настроенным вручную OpenVPN-серверам без полного понимания последствий.

---

## 📦 Поддерживаемые ОС

Роль наследует поддержку ОС от оригинального скрипта:

- **Debian** 12+
- **Ubuntu** 22.04+

> 🔧 Требуется `systemd` и включенный TUN-модуль.

---

## 🚀 Возможности

- Автоматическая установка и настройка OpenVPN
- Генерация клиентских конфигураций (`.ovpn`)
- Поддержка автоматического (headless) режима
- Идемпотентность: безопасно запускать повторно
- Управление клиентами: добавление новых пользователей
- Безопасные настройки по умолчанию (AES-128-GCM, TLS 1.2+, tls-crypt и др.)

---

## ⚙️ Переменные

Основные настраиваемые параметры (указываются в `vars`, `group_vars` или при вызове роли):

| Переменная             | По умолчанию       | Описание |
|------------------------|--------------------|---------|
| `openvpn_clients`      | `["client1"]`      | Список имён клиентов для генерации конфигураций |
| `openvpn_script_path`  | `/root/openvpn-install.sh` | Путь к скрипту на целевом хосте |
| `openvpn_download_url` | URL к `raw.githubusercontent.com` | Откуда скачивать скрипт |
| `openvpn_port`         | 1195               | Порт работы OpenVPN |
| `nginx_port`           | 80                  | Порт работы Nginx |

Пример использования:

```yaml
openvpn_clients:
  - laptop
  - phone
  - tablet
openvpn_recreate: true
```
---

## ✅  Доступ

После первого запуска роли файл с данными для доступа в панель filebrowser находится в домашней директории пользователя от котороо был запущен процесс установки.

---