# 🚫 proxmox-disable-subscription-popup

Ein einfaches Bash-Skript zur Deaktivierung der lästigen **"No valid subscription"**-Popup-Meldung in der Weboberfläche von [Proxmox VE](https://www.proxmox.com/), insbesondere nützlich bei Nutzung der kostenlosen **Community Edition**.

> ⚠️ **Hinweis:** Dieses Skript verändert nur die grafische Oberfläche (JavaScript) und umgeht keine Lizenzprüfung. Es wird **keine Subscription-Funktionalität simuliert oder freigeschaltet**.

---

## ✨ Funktionen

- 🔧 Entfernt das "No valid subscription"-Popup beim Login
- 🔁 Wiederverwendbar nach jedem Proxmox-Update
- 🕒 Erstellt automatische Backups mit Zeitstempel
- ✅ Minimal-invasiv & leicht rückgängig zu machen

---

## 📂 Verzeichnisstruktur

```text
/
├── disable-subscription-popup.sh   # Hauptskript
├── LICENSE                         # MIT-Lizenz
└── README.md                       # Diese Datei
```

---

## 🛠️ Verwendung

### 1. Skript herunterladen
```bash
wget https://raw.githubusercontent.com/<DEIN-GITHUB-NAME>/proxmox-disable-subscription-popup/main/disable-subscription-popup.sh
chmod +x disable-subscription-popup.sh
```

### 2. Skript ausführen
```bash
sudo ./disable-subscription-popup.sh
```

Das Skript:
- sucht nach dem Popup-Code in `/usr/share/javascript/proxmox-widget-toolkit/proxmoxlib.js`
- erstellt ein Backup: `proxmoxlib.js.bak.YYYYMMDD-HHMMSS`
- kommentiert den Popup-Block aus
- startet den Webdienst neu

---

## 🔁 Automatisierung (optional)

### Cronjob bei jedem Neustart:
```bash
crontab -e
```
Einfügen:
```bash
@reboot /root/disable-subscription-popup.sh
```

---

## 🧯 Wiederherstellung

Wenn du die Originaldatei wiederherstellen möchtest:

```bash
cp /usr/share/javascript/proxmox-widget-toolkit/proxmoxlib.js.bak.<ZEITSTEMPEL> /usr/share/javascript/proxmox-widget-toolkit/proxmoxlib.js
systemctl restart pveproxy
```

---

## 📄 Lizenz

Dieses Projekt steht unter der [MIT License](LICENSE).

---

## 💬 Feedback & Mitmachen

Fehler gefunden? Verbesserungsideen?  
Erstelle gerne ein [Issue](https://github.com/<DEIN-GITHUB-NAME>/proxmox-disable-subscription-popup/issues) oder sende einen Pull Request.

---

## 🙏 Danke

An die Proxmox-Entwickler für eine großartige Plattform – und an alle Open-Source-Beitragenden, die freie Software verbessern.
