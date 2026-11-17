# gosip

> SIP stack in Go ([RFC 3261](https://tools.ietf.org/html/rfc3261))

[![Build Status](https://travis-ci.org/ghettovoice/gosip.svg?branch=master)](https://travis-ci.org/ghettovoice/gosip)
[![Coverage Status](https://coveralls.io/repos/github/ghettovoice/gosip/badge.svg?branch=master)](https://coveralls.io/github/ghettovoice/gosip?branch=master)

## Fork maintenance

Update this section in the same change as every fork-specific code or dependency update. Record the date, the behavior that changed, and how it was verified. Include the affected maintenance branch or pinned revision when applicable.

### 2026-11-17 — Client SIP transaction registration

- Register client transactions before the initial send so an immediate response matches its Via branch and CSeq method.
- Process the response after the initial write and timer setup. Remove the exact transaction if the write fails or the layer closes, and keep the original transaction when a duplicate key is submitted.
- Deterministic tests cover immediate responses to UDP and TCP INVITE and MESSAGE, retries after send failure, shutdown during send, and duplicate keys. Verified with `go test -race -count=1 ./transaction`.
- The patch is available on the current fork and on the [d58873a compatibility revision](https://github.com/X-mediastream/gosip/commit/2edc6fc4d9c9ef6d30fd52bce1408c745bdab3da).

## PROJECT IS UNDER DEVELOPMENT

Inspired by:
- [gossip](https://github.com/StefanKopieczek/gossip)
- [go-sip](https://github.com/1lann/go-sip)
- [sip.js](https://github.com/kirm/sip.js)
