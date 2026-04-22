# Changelog

Notable changes to the 3ncr.org specification site and the v1 envelope it
documents. The envelope format itself (`3ncr.org/1#<base64(iv || ciphertext || tag)>`,
AES-256-GCM, 12-byte IV, 16-byte tag) is stable; entries below tighten the
accompanying prose, add guidance, or extend the test-vector corpus.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

## 2026-04-22

### Added

- Official-implementations list on `/1/` now covers all eight libraries
  (Go, Node.js, PHP, Python, Rust, Java, C#, Ruby). (#7)
- Canonical v1 test-vectors table on `/1/#testing`, cross-verified against
  the Go reference and the Node port; pre-loaded into the browser demo. (#4, #6)
- Empty-string and long multi-sentence ASCII vectors added to the corpus to
  cover edge cases. (#6)
- Self-contained browser encrypt/decrypt demo at `/1/demo/`, built on
  WebCrypto with no external dependencies. (#5)
- Envelope binary layout and base64 encoding documented explicitly on `/1/`:
  `iv[12] || ciphertext[variable] || tag[16]`, base64 **without** padding;
  decoders should accept either form for robustness. (#3)
- Tiered KDF guidance on `/1/#kdf`: raw 32-byte key (primary), Argon2id
  (`m=19456 KiB, t=2, p=1`, 32-byte output, salt ≥ 16 bytes) for passwords,
  SHA3-256 single hash for high-entropy secrets. The envelope remains
  KDF-agnostic. (#2)

### Changed

- PBKDF2-SHA3 `(secret, salt, iterations=1000)` is labelled **legacy** in the
  spec — kept only so existing data remains decryptable; new code should use
  a raw key or Argon2id. (#1)
- Copyright on `LICENSE`, `/1/index.html`, and `/1/demo/index.html` updated
  to `2018-2026`; personal email removed from the `/1/` footer. (#7)

## 2018

Initial publication of the `3ncr.org/1#` envelope specification.

[Unreleased]: https://github.com/3ncr/3ncr.org/compare/master...HEAD
