# coexistgate-demo

Tiny shop service used as **public proof** for [CoexistGate](https://github.com/devcy0922/coexistgate).

Pull requests look like normal application changes. Build and tests pass. CoexistGate reports whether the change can be released and rolled back.

| PR | Scenario | Expected |
| --- | --- | --- |
| Unsafe DB migration | `RENAME COLUMN email` while previous code still uses `users.email` | FAIL |
| Safe DB expand | `ADD COLUMN email_address` keeping `email` | PASS |
| Availability | `replicas: 3` → `1` vs `minimum_replicas: 2` | FAIL |
| Config rollback | `REDIS_URL` replaced by `CACHE_URL` | FAIL |
