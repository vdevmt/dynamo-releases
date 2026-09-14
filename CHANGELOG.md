# Changelog

*English · [Italiano](CHANGELOG.it.md)*

What changes for whoever uses the program, newest first. Every version is published as an
[installer package](../../releases) for Windows x64, in two setup languages.

---

## 1.48.5 — scheduled operations and data upgrades

Online, an extension can now be published in the environment's update window, and a new
**Scheduled operations** window lists what will run later on its own — extensions waiting for the
update window or the next update, app updates, the next environment update — and cancels what
Business Central allows. In Extension Management a per-tenant extension with a new version already
scheduled says so, and the schedule can be removed from there. On premises, publishing no longer
fails when Business Central requires a data upgrade — for example after the previous version was
uninstalled with its data still there: the upgrade runs, or can be left for later with the new
**Upgrade data** command and the **Data upgrade** column of Extension Management. The toolbar now
adapts to the window width, and tabs show the target type with an icon.

---

## 1.48.4 — safer operations on production systems

A review of every operation that writes to Business Central tightened the points where a command
did more than its confirmation said. On premises, an extension that other installed extensions
depend on is no longer uninstalled — they are listed and must go first, as online — and
republishing the same version in ForceSync now puts those extensions back, with their data.
Confirmations name the real server or tenant of every target, the second ForceSync confirmation
starts on "No", an online environment is checked again right before it is deleted, and an imported
list is checked before it is used. Lists of extensions are easier to read, and the activity queue
keeps its colors in English too.

---

## 1.48.3 — report problems, simpler update checks

You can now report a problem or suggest something straight from the "?" menu or the About window:
both open a ready-to-fill form on this page. Checking for updates is now a simple on/off switch,
checked automatically every time the program starts, instead of a day count. The installer can
open DYNAMO automatically right after setup, with a checkbox on the last page. A few smaller
interface fixes round out the release.

---

## 1.48.2 — interface refinements

This release reorganizes a few commands and optimizes the layout in several areas of the
interface.

---

## 1.48.1 — toolbar follows the destination

The toolbar now shows only the buttons that make sense for the selected tab: service commands and
license stay OnPrem-only, a new Admin Center button opens the SaaS tenant portal, and a new Events
button opens an environment's event log. On an environment in the recycle bin, only restoring it
stays available until it comes back.

---

## 1.48.0 — first release

The first version published here, with the complete feature set of the program. Earlier versions
were not distributed.

---

Release notes for versions before 1.48.0 are available on request.
