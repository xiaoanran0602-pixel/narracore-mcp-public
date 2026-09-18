# Privacy

Short version: your text is used to produce your result, nothing else.

- **Input text** is processed in memory to produce your blocks/PDF. It is not used for training, not shared, not shown to other users.
- **Film breakdowns**: your video is never uploaded. Your agent observes the footage locally; only the structured breakdown text reaches this service, and it is not persisted as database records.
- **Story continuity**: the full manuscript and the returned `StoryState` stay on your side. Submitted turns and state are handled only while a request is being processed.
- **Generated PDFs** are stored only to serve you the download link and are **deleted after 24 hours**.
- **License keys** are stored as SHA-256 hashes (plus last 4 characters for display). We never store plaintext keys after issuance.
- **Payments** are processed by PayPal; we receive your email (from the PayPal order) and the payment amount only. No card data touches our servers.
- **Logs** contain request metadata (timestamps, request id, page counts, error codes) — not your manuscript content. The web server also keeps an access log (request time, path, status, user agent, IP address) that rotates out automatically at a fixed size cap. Query strings are stripped before writing, so license keys and PDF signatures never reach the log file.
- **Free-tier limiting** stores a hashed, IP-derived fingerprint in the application database rather than the IP itself — a SHA-256 of the IP together with the UTC date. The input space (IP addresses × dates) is small, so treat this as pseudonymous rather than truly anonymous. The daily visitor count uses a separately-salted hash in the same style.
- **No accounts, no cookies, no trackers, no newsletters.**

Questions or data removal requests: **huiyicd@foxmail.com**
