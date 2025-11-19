# **KDBX Sync Bridge — Roadmap**

A simple local-to-cloud sync system designed for KeePass (**.kdbx**) files.  
Directly editing files inside Google Drive or other cloud-mounted folders is unreliable.  
This project solves that using a safe workflow:

**Local Copy → Edit → Sync Back to Cloud**

---

## **v0.1.0 – Minimal Working Version (MWV)**  
**Goal:** Basic safe syncing with Google Drive.

### **Features**
- Authenticate with Google Drive (PyDrive)  
- Download cloud file to a local working copy  
- Detect changes in the local file  
- Upload back to Google Drive safely  
- Use temporary files during upload  
- Simple config file (`file_id`, `local_path`, `interval`)  
- Basic logging  

### **Focus**
- Implement `download()`  
- Implement `upload()`  
- Implement file change detection  
- Make sync loop stable  

---

## **v0.2.0 – Safety Layer**  
**Goal:** Prevent corruption and data loss.

### **Features**
- Local lock file (`.lock`)  
- Keep last **5** cloud versions  
- Hash verification before upload  
- Temporary files (`file.tmp → file`)  
- Retry on network failure  
- Better error logs  

---

## **v0.3.0 – Multi-Device Conflict Handling**  
**Goal:** Avoid overwriting changes from other devices.

### **Features**
- Compare local hash vs cloud hash  
- Conflict detection  
- Auto-create conflict copy (`conflict-timestamp.kdbx`)  
- Alert user on conflict  
- Track `last_sync_hash`  

---

## **v0.4.0 – Background Sync Daemon**  
**Goal:** Make it automatic and invisible.

### **Features**
- Run as a Linux systemd service  
- Background monitoring loop  
- CLI commands (`start`, `stop`, `status`, `force-pull`, `force-push`)  
- Simple status logging  

---

## **v0.5.0 – User Experience Improvements**  
**Goal:** Make configuration and usage easier.

### **Features**
- Setup wizard to generate config  
- Desktop notifications on sync  
- Conflict warnings  
- Log viewer  
- Optional system tray UI  

---

## **v0.6.0 – Multi-Cloud Support**  
**Goal:** Sync with more than Google Drive.

### **Add Providers**
- Dropbox  
- OneDrive  
- WebDAV / Nextcloud  
- Local NAS folders  

### **Unified Provider Interface**
- `download`  
- `upload`  
- `get_hash`  
- `list_versions`  

---

## **v0.7.0 – Security & Verification**  
**Goal:** Make the sync extremely reliable.

### **Features**
- SHA-256 integrity checks  
- Optional additional encryption layer  
- Secure temp file handling  
- Signed sync logs  
- Verification commands  

---

## **v0.8.0 – Python Package Release**  
**Goal:** Make it installable and developer-friendly.

### **Features**
- Publish to PyPI  
- `pip install kdbx-sync-bridge`  
- CLI help and docs  
- Type hints  
- Examples and templates  

---

## **v1.0.0 – Stable Release**  
**Goal:** A polished, reliable cloud-sync bridge.

### **Features**
- Stable multi-device sync  
- Background service by default  
- Safety and conflict protection  
- Multi-cloud provider support  
- Full documentation  
- Community-ready GitHub repo  
