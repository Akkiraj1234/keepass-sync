# KDBX Sync Bridge

A simple local-to-cloud sync system designed for KeePass (**.kdbx**) files.  
Directly editing files inside Google Drive or other cloud-mounted folders is unreliable.  
This project solves that by using a safe workflow:

**Local Copy → Edit → Sync Back to Cloud**

---

## Table of Contents
- [Overview](#overview)
- [Roadmap](#roadmap)
  - [v0.1.0 – Minimal Working Version](#v010--minimal-working-version-mwv)
  - [v0.2.0 – Safety Layer](#v020--safety-layer)
  - [v0.3.0 – Multi-Device Conflict Handling](#v030--multi-device-conflict-handling)
  - [v0.4.0 – Background Sync Daemon](#v040--background-sync-daemon)
  - [v0.5.0 – User Experience Improvements](#v050--user-experience-improvements)
  - [v0.6.0 – Multi-Cloud Support](#v060--multi-cloud-support)
  - [v0.7.0 – Security & Verification](#v070--security--verification)
  - [v0.8.0 – Python Package Release](#v080--python-package-release)
  - [v1.0.0 – Stable Release](#v100--stable-release)

---

## Overview

KeePass files are not safe to edit directly in cloud-mounted drives like Google Drive or Dropbox.  
**KDBX Sync Bridge** provides a safe workflow:

1. Download cloud file to a local copy  
2. Edit locally  
3. Sync changes back safely  

It supports multi-device syncing, conflict detection, and multiple cloud providers.

---

## Roadmap

### v0.1.0 – Minimal Working Version (MWV)
**Goal:** Basic safe syncing with Google Drive

**Features**
- Authenticate with Google Drive (PyDrive)
- Download cloud file to local working copy
- Detect local changes
- Safe upload with temp files
- Simple config (`file_id`, `local_path`, `interval`)
- Basic logging

**Focus**
- Implement `download()`
- Implement `upload()`
- File change detection
- Stabilize sync loop

---

### v0.2.0 – Safety Layer
**Goal:** Prevent corruption and data loss

**Features**
- Local `.lock` file
- Keep last 5 cloud versions
- Hash verification before upload
- Temp-file upload flow
- Retry on network failure
- Improved error logs

---

### v0.3.0 – Multi-Device Conflict Handling
**Goal:** Avoid overwriting cloud changes

**Features**
- Compare local vs cloud hash
- Conflict detection
- Auto-create conflict copy (`conflict-timestamp.kdbx`)
- Alert user on conflict
- Track `last_sync_hash`

---

### v0.4.0 – Background Sync Daemon
**Goal:** Fully automatic, invisible syncing

**Features**
- Run as Linux systemd service
- Background monitoring loop
- CLI commands: `start`, `stop`, `status`, `force-pull`, `force-push`
- Simple status logging

---

### v0.5.0 – User Experience Improvements
**Goal:** Make configuration and usage easier

**Features**
- Setup wizard
- Desktop notifications
- Conflict warnings
- Log viewer
- Optional system tray UI

---

### v0.6.0 – Multi-Cloud Support
**Goal:** Sync with more than Google Drive

**Providers**
- Dropbox
- OneDrive
- WebDAV / Nextcloud
- Local NAS folders

**Unified Provider API**
- `download()`
- `upload()`
- `get_hash()`
- `list_versions()`

---

### v0.7.0 – Security & Verification
**Goal:** Make the sync extremely reliable

**Features**
- SHA-256 integrity checks
- Optional extra encryption layer
- Secure temp-file handling
- Signed sync logs
- Verification commands

---

### v0.8.0 – Python Package Release
**Goal:** Installable and developer-friendly

**Features**
- Publish on PyPI
- `pip install kdbx-sync-bridge`
- CLI help and docs
- Type hints
- Example configs/templates

---

### v1.0.0 – Stable Release
**Goal:** Production-ready cloud-sync bridge

**Features**
- Stable multi-device sync
- Background service by default
- Safety and conflict protection
- Multi-cloud support
- Full documentation
- Community-ready GitHub repo
