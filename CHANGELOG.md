# Changelog

*English · [Italiano](CHANGELOG.it.md)*

What changes for whoever uses the program, newest first. Every version is published as an
[installer package](../../releases) for Windows x64, in two setup languages.

---

## 1.49.0 — AppSource catalog, web services and APIs, local history

**New features**
- **AppSource catalog**: every Business Central app published for the environment's market, already
  listed and filterable by name and publisher, with the full details of each one. You install them
  from there, or update them if they are already installed.
- **Web services and APIs** (new Development menu): what a target exposes over OData V4, API and
  SOAP — installed apps' APIs included — with ready addresses, fields, methods and sample request,
  response and error to paste into a technical document.
- **AL symbols**: from Extension Management you download the symbols of the apps installed on a
  target, from the public feeds or straight from the target, which also provides those of
  per-tenant extensions. From the Development menu, "Download Microsoft symbols" fetches from the
  public feeds the symbols of Microsoft apps for a localization and a version, with no target
  needed.
- **Local history**: the operations that change a target, started from this computer, are kept in a
  local log with the options chosen, the steps run and the error message, if any.
- **Links in the tab**: next to the targets, a tab with the websites, folders and network shares
  that belong to them — the customer's portal, the documentation, the package folder.

**Job queue**
- **Extension operations wait until the target is ready**: before any operation on an extension,
  DYNAMO checks that the online environment is not being updated and has no other deployment
  running — a colleague's, from VS Code or from inside Business Central —, and on a server that the
  instance service is running. If the target is busy the operation stays queued and starts on its
  own as soon as it frees up; "Start now" skips the wait.
- **Retry from the queue**: an unsuccessful row runs again with the options of the first attempt,
  without going back through the menu; "Retry unsuccessful" runs them all again at once.

**Targets**
- **Details card**: shows the open sessions and, on online environments, the running deployments —
  the two things to know before stopping a service or starting a publish. Next to the Business
  Central version, "What's new in …" opens Microsoft's release notes for that update, and the same
  next to the target version of the next one.

**Other changes**
- **Add tab** replaces "Add server" and "Add tenant", and offers a third type: a tab with no
  targets, made of links only. An on-premises tab now stays in the list even when the discovery
  finds no services.
- Links can be gathered into **groups**, which travel with the exported list.
- A new **Scheduled** outcome in the queue, for what the environment accepted but has not run yet,
  kept apart from *Skipped*, which will not happen.
- In Extension Management an app with an available update says **Update available** in the Status
  column.
- The column a grid is sorted by shows an arrow, and the activity queue always stays in arrival
  order.
- On start, with Business Central installed on the computer, the localhost tab is ready and realigns
  itself with the installed instances; opening the web client, the company used last is at the top
  of the list.

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
