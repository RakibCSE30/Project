# Data Privacy & Secret Management

## Secret Management
* **Never commit secrets:** Any `.env`, private keys, or API tokens pushed to the repository will trigger an automatic security alert and require immediate key rotation.
* Use GitHub Secrets for production environment injections.

## Compliance
* Passwords must be hashed using `bcrypt` with a salt round of 10.
* Session tokens (JWT) must expire within 15 minutes.