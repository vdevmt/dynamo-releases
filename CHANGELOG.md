# Changelog

*English · [Italiano](CHANGELOG.it.md)*

What changes for whoever uses the program, newest first. Every version is published as an
[installer package](../../releases) for Windows x64, in two setup languages.

---

## 1.47.0 — first public release

The first version published here. Earlier versions were not distributed.

What it does, at this version:

- **Targets of both kinds in one list.** Every tab is an on-premises server or an online tenant;
  the rows are the service instances or the environments. Tabs are renamed, coloured and reordered,
  rows are hidden and shown, and a Favourites tab collects rows taken from different tabs.
- **Read-only readiness test** on every target, which reports whether the service answers and
  whether the account is allowed to work on it, before anything is changed.
- **Start, stop and restart** of on-premises services, on as many targets as you highlight.
- **Extension management**: install, uninstall, unpublish and synchronize, with the state of every
  extension, its publisher, its version and — on premises — whether it has been synchronized.
  Uninstalling never deletes data.
- **Publishing** of a single package or of a whole folder, in the order derived from the
  dependencies declared inside each one, with the order shown and adjustable before you confirm and
  one queue row per app.
- **Comparison of the extensions** of two targets, even of different kinds, and of the
  **configuration of two on-premises instances**, showing only the keys that differ.
- **Online environments**: create, copy, rename, delete, restore to a point in time or from the
  recycle bin, set the update window, schedule the update, read the event log, and update
  marketplace apps with the whole dependency chain queued in the right order.
- **The web client opens on the company you choose**, so the Business Central company selection
  does not appear; on a server the question comes only where no default company is declared.
- **Configurations for VS Code**: the one to develop against a target, and the attach one for a
  session that is open right now, taken from Active sessions.
- **Companies, active sessions and the Business Central license** of a target, with the ability to
  end a session and to load a license file.
- **An activity queue** that works one lane per target — in sequence inside a lane, in parallel
  across lanes — with the outcome, the duration and the full error of every operation kept until
  you clear it.
- **English and Italian**, including numbers, dates and durations, chosen in Settings and
  independent of the language of Windows.
- **Anonymous usage counts**, switched off any time in Settings, say which commands get used and on
  which Business Central version — plus how many on-premises servers and online tenants are in the
  list, and how many distinct accounts reach the on-premises servers. Never a name, a path or the
  text of an error.
- **The installer package is smaller**: it now carries only the support files English and Italian
  actually need.

---

Release notes for versions before 1.47.0 are available on request.
