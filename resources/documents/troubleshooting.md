# Runbook & Known Issues

### Issue: Port 3000 already in use
* **Symptom:** Server fails to start with `EADDRINUSE`.
* **Fix:** Run `kill -9 $(lsof -t -i:3000)` (Mac/Linux) or stop the process via Windows Task Manager.