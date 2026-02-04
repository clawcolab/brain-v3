# Changelog

## [0.1.6] - 2026-02-04

### 🚀 One-Command Install

ClawBrain is now truly plug-and-play. Install with a single command:

```bash
curl -fsSL https://raw.githubusercontent.com/clawcolab/clawbrain/main/remote-install.sh | bash
```

Then restart your service:
```bash
sudo systemctl restart clawdbot  # or openclaw
```

**That's it!** No configuration required. Works out of the box with SQLite.

---

### ✨ New Features

- **Auto-refresh on startup** - Brain automatically loads memories when service restarts
- **Session save on /new** - Saves conversation context when user starts new session
- **Native hooks support** - Works with both ClawdBot and OpenClaw
- **Auto-detection** - Detects platform, skills directory, and storage backend automatically
- **PostgreSQL datetime fix** - Properly handles datetime serialization from PostgreSQL

### 🔧 Configuration (Optional)

All configuration is optional. Set environment variables only if needed:

| Variable | Description | Default |
|----------|-------------|---------|
| `BRAIN_AGENT_ID` | Unique ID for memories | `default` |
| `BRAIN_POSTGRES_HOST` | PostgreSQL host | SQLite used |
| `BRAIN_REDIS_HOST` | Redis for caching | Disabled |

### 📁 New Files

- `install.sh` - Local installer script
- `remote-install.sh` - Curl-based remote installer
- `hooks/clawbrain-startup/` - Native hook for gateway events
- `scripts/brain_bridge.py` - Python bridge for hook→brain communication
- `scripts/migrate_agent_id.py` - Utility to migrate memories between agent IDs

### 🐛 Bug Fixes

- Fixed PostgreSQL datetime objects not serializing to JSON
- Fixed UserProfile datetime fields from PostgreSQL
- Fixed skills directory detection for different platform layouts

---

**Full Changelog**: https://github.com/clawcolab/clawbrain/compare/v0.1.5...v0.1.6
