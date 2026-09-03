<img src="assets/banner.png" alt="DYNAMO — Management &amp; Operations for Microsoft Dynamics 365 Business Central" width="470">

*English · [Italiano](README.it.md)*

Administration console for **Microsoft Dynamics 365 Business Central**, on premises and online,
from one window.

Every tab is a **server** (on premises) or a **tenant** (online); the rows are the service
**instances** or the **environments**. From there you check that a target is reachable, start and
stop services, publish and manage extensions, read and compare service configurations, see who is
connected, and open the web client on the company you want — across many targets at once, with the
outcome of every operation kept in a queue you can read at your own pace.

**[Download the latest version](../../releases/latest)** · [Changelog](CHANGELOG.md) ·
[License](LICENSE) · [Usage data](PRIVACY.txt)

| | On premises | Online |
|---|---|---|
| Readiness test | ✔ | ✔ |
| Start / Stop / Restart | ✔ | — (there is no service to start) |
| License information and loading | ✔ | — (licenses are M365 subscriptions) |
| List of installed extensions | ✔ | ✔ |
| Install / uninstall / unpublish an extension | ✔ | ✔ (unpublish needs BC 25.4+) |
| Extension schema synchronization | ✔ | — (the platform does it during the deployment) |
| Publishing (single .app or whole folder) | ✔ | ✔ |
| Reading and changing the service configuration | ✔ | — (no API exposes it) |
| Environment operations (copy, restore, update window) | — | ✔ |

---

## Download and install

Two installer packages are published with every release. They differ **only in the language of the
setup windows** — the installed application is the same and is bilingual either way:

    dynamo-<version>-x64-en.msi    setup in English
    dynamo-<version>-x64-it.msi    setup in Italian

Double click the file. Setup shows the license agreement and asks you to accept it, then asks three
things: the destination **folder** (`C:\Program Files\Dynamo` by default), which **shortcuts** to
create, and the default **language**. The installation is per machine, so the shortcuts appear for
every user and administrator rights are required.

Prefer a short destination path: the file tree already reaches 102 characters on its own, and past
260 in total Windows can no longer write.

The package is **not signed**: Windows shows "Unknown publisher" on the elevation prompt.

### Upgrading and uninstalling

To upgrade, run the installer of the new version: the previous one is removed and replaced in one
go, with nothing to uninstall first and no old files left behind. To uninstall: *Windows Settings >
Apps > Installed apps > DYNAMO*.

Running the installer of the version already installed, or choosing *Modify* next to the entry in
Installed apps, opens the maintenance page with the three usual choices — **Change** (shortcuts and
default language), **Repair** (puts back missing or damaged files) and **Remove**.

Neither upgrading nor uninstalling loses your list, tabs, online connections or preferences: they
live in your user profile and are not touched. To remove those as well, delete the folder by hand.

### Silent installation

    msiexec /i dynamo-<version>-x64-en.msi /qn

The same choices offered by the screens can be set on the command line:

    msiexec /i dynamo-<version>-x64-en.msi /qn ^
            INSTALLFOLDER="D:\Apps\Dynamo" ^
            APPLANGUAGE=en INSTALLDESKTOPSHORTCUT=0 INSTALLSTARTMENUSHORTCUT=1

`APPLANGUAGE` is `en` or `it`; the two shortcut properties are `1` (create) or `0` (do not create).
To uninstall silently, with the same file: `msiexec /x dynamo-<version>-x64-en.msi /qn`.

---

## Requirements

**On the PC running the tool** — nothing to install: the .NET runtime is included in the package.
Windows 10/11 or Windows Server, x64. The program starts with your own rights and does **not** ask
for UAC. Administrator rights are needed only for Business Central instances installed on that same
computer; where they are needed and you do not have them the commands stay switched off and the
status bar says so, so nothing fails halfway through. *Tools > Restart as administrator* restarts
the program with the rights. Working on remote servers or online never needs any of this.

**On the on-premises Business Central servers** — Windows PowerShell 5.1 with the Business Central
administration module installed; PowerShell Remoting (WinRM) enabled, with the loopback allowed for
services on the same machine; an account permitted to manage the services and publish extensions.

**For online environments** — connectivity to `api.businesscentral.dynamics.com` and
`login.microsoftonline.com`; a browser to sign in with; a Business Central administrator account on
the tenant. With the default sign-in mode there is nothing to prepare in Azure.

---

## First run — building the list

The list starts **empty**.

- **On premises**: *Tools > Add server*. Give the server name and the Business Central services
  installed on it are discovered and added to the tab.
- **Online**: *Tools > Add tenant*. Give the tenant domain (`contoso.onmicrosoft.com`) or its
  identifier, and the environments are listed after you sign in.

The list saves itself on every change. It can be **exported and imported**, so a colleague can start
from yours without retyping anything — your own preferences are never carried along with it.

### Signing in to a tenant

Two ways, neither of which keeps a secret on the machine:

- **Code sign-in — the default.** The program shows a code; you type it in the browser at the
  address shown, even from another device, and sign in with your company account, MFA included. The
  operation then resumes on its own. **It needs no preparation in Azure**: a tenant you have just
  added works straight away.
- **Direct sign-in through an app registration.** The browser opens immediately and the sign-in
  completes with no code to type. This one needs an application registration in Microsoft Entra ID,
  done once per organisation by a tenant administrator: a registration of type *public
  client/native* with `http://localhost` as the redirect URI, the delegated permission
  *user_impersonation* on Dynamics 365 Business Central, admin consent granted, and public client
  flows allowed. Then paste the application (client) ID into the connection dialog — it is the only
  value to enter.

No client secret is needed in either case. The settings are **per tenant**, so different customers
can have different registrations and even different clouds, and the sign-in token is kept in an
encrypted cache in your own Windows profile.

---

## What you can do

### Services and status

*Check status* is a **read-only** test: it reports, target by target, whether the service is
reachable and whether the account is allowed to work on it. Use it first — it changes nothing.

*Start*, *Stop* and *Restart* act on every highlighted row; *Restart* skips what is not running.
They are disabled on online tabs, where there is no service to command.

### The target

- **Details card** — everything the target declares about itself: type, status, version, and for
  online environments the next update, the country, region and geography, the database size and the
  web addresses, selectable so they can be copied. For an on-premises instance, the server, the
  instance, the Windows service name and the administration module path actually used, which is the
  first thing to look at when the module fails to load. Values Business Central does not provide
  stay empty rather than being guessed.
- **Open web client** — opens the environment or the instance in your default browser, on the
  company you choose, so the Business Central company selection does not appear. The company you
  picked last on that target comes back selected; with a single company it opens straight away. On
  a server the question comes only where the service does not already declare a default company.
- **Configuration for VS Code** — produces the configuration to paste into `launch.json` to develop
  against that target, with the values read from the service. From *Active sessions* you also get
  the attach configuration for the highlighted session, ready to use.
- **Company list** — name, display name and identifier of the companies, copyable.
- **Active sessions** — who is connected, and the ability to end a session.
- **License information** — reads the Business Central license of an on-premises instance, and
  loads a new one.

### Extensions

**Extension management** reads the extensions of the current target and shows them with name,
publisher, version, state, how they were published and their identifier. It sorts by column and
filters on three axes that combine: state, publisher and free text. From there you synchronize,
install, uninstall and unpublish.

Uninstalling **never deletes data**, on any target type: the command that would erase an
extension's tables is not reachable from here. On online environments the confirmation first tells
you what depends on the extension and must go first, and whether a version is already scheduled —
which matters, because uninstalling does not remove a scheduled version and the extension would
reinstall itself later on its own.

Only on premises there is a **Sync** column: an extension published but not synchronized does not
work, and that is not visible anywhere else.

**Publishing** takes a single `.app` or a whole folder, and works out the order from the
dependencies declared inside each package. The order is shown before you confirm and **can be
changed** — moving an app before one it depends on warns you but does not stop you, because that
dependency may already be installed. Each app gets its own row in the queue, with state, duration
and error, so you can leave the desk and see on your return what went through. If one app fails the
others go on; only those that depended on it are skipped, because they would fail anyway.

**Compare extensions** puts the extensions of two targets side by side — even targets of different
kinds, on different tabs — and shows what differs.

**Linked apps** answers the question you ask before removing anything: what breaks if this
extension goes away.

### Online environments

Create, copy, rename and delete an environment; restore it to a point in time or from the recycle
bin; set the update window and schedule the update; and read the environment's event log — creation,
copy, rename, deletion, updates, app installations.

**App updates** live inside extension management: the *Available version* column carries the version
you can move to, and you update either straight away or in the environment's update window. Apps
that have to be updated first are queued too, and before it: the confirmation lists the whole chain
in the order it will happen. This covers apps installed from the marketplace, partner apps included;
per-tenant extensions have no available version here — they are updated by publishing the new
package.

### Service configuration (on premises)

All the configuration keys of an instance, grouped by area and with the description of what each one
does. Two instances can be **compared**, showing only the keys that differ — the fastest way to find
out why one server behaves unlike another. A key can be changed from here, behind a confirmation
that names the instance.

---

## The activity queue

The grid at the bottom is a **basket**: operations do not start straight away, they are queued, and
more can be added while the queue is running. Nothing wipes the results of the previous operation.

There is one rule: **one lane per target**. Inside a lane the activities run in sequence, in the
order you asked for them; different lanes run in parallel. Ask for "extension X on A", "extension X
on B", "extension Y on A" and finally "restart A", and X on A and X on B start together, Y on A
starts when X on A has finished, and the restart of A comes after Y — without waiting for B, which
is on another lane.

*Max targets in parallel* limits the lanes, so it applies to the whole queue, and it can be changed
with the queue full: raising it starts the waiting targets immediately, lowering it interrupts
nothing already started.

The **x** at the end of a row appears only on rows still queued, and removes that row only: a job
already running is not interrupted, because stopping a publish halfway would leave the service in an
uncertain state. Closing the application with a full queue asks for confirmation — and the
interruption stops the application, not what the server has already started.

### Reading the results

The status text is coloured: green completed, red error, amber skipped, blue running. A truncated
error opens in full with the **...** button, and the message at the bottom of the window opens in a
readable window when you click it.

When a publish to an online environment fails, the reason written by Business Central is reported
**in the job**, with the time and the identifier of the operation, so there is nothing else to open.
Two cases have no reason to report — a package over 50 MB, and an environment that cannot report it
yet — and the job says so instead of leaving you guessing.

*Check status* produces an itemised report: one row per check, with outcome and cause, failed rows
highlighted.

---

## Selection and confirmations

Rows are chosen with the **standard Windows selection**: click, Ctrl+click to add or remove,
Shift+click for a range, Ctrl+A for all. There are no menu entries for selection — the grid does it,
as in any other Windows list. The selection of each tab survives a tab change.

Two notions matter: the **highlighted rows**, on which the commands that accept several targets act,
and the **current row**, the last one you clicked, on which the commands that accept only one act.
With a single highlighted row the two coincide, which is the normal case.

Every function acting on several rows asks for **confirmation, saying how many and which targets
will be touched**. Confirmations that would interrupt a service start on "No".

---

## Where the settings live

| | |
|---|---|
| List, tabs and online connections | `%APPDATA%\Dynamo\environments.json` |
| Preferences (language, parallelism, refresh) | `%APPDATA%\Dynamo\settings.json` |
| Sign-in token cache (encrypted) | `%LOCALAPPDATA%\Dynamo\` |
| On-premises server accounts | Windows Credential Manager, `DYNAMO:<server>` |

*File > Settings* shows the path of the folder and opens it: that is the folder to copy for a
backup, or to move the configuration to another machine.

They are **two files on purpose**. The list is exported and shared; the preferences belong to
whoever uses the machine — so importing a colleague's list does not take your own configuration
away.

---

## Language and regional settings

The application speaks **English or Italian**, chosen in *File > Settings*. The first run starts from
the Windows language and writes it into the configuration; from then on your choice rules, not the
machine. On a Windows that is neither, it starts in English. The change takes effect at the next
start — windows already built do not rewrite themselves — and the dialog says so when you confirm.

Numbers and dates follow the **chosen language**, not the Windows one: a duration reads `8.4s` in
English and `8,4s` in Italian.

Messages coming from Business Central, from PowerShell or from Windows stay in the language of
whoever produced them and are not translated: rewriting them would mean inventing them.

---

## Security and careful use

The tool acts on production systems, and it is built to make that safe rather than fast.

- **The commands it can run are a fixed, closed set.** Nothing arbitrary can be executed through it,
  and every value it passes to Business Central travels as a parameter, never as text glued into a
  command. The exact list of the commands used is written out in the guide included in the package,
  where it serves as a guarantee of what the program really runs.
- **Every destructive operation is confirmed by name.** The confirmation says which targets are
  about to be touched, and the ones that would interrupt a service start on "No".
- **The read-only test changes nothing.** Use it first to check connectivity and permissions.
- **Sign-in to online tenants is interactive**, against Microsoft Entra ID with a public client:
  no secret is stored on the machine. The token stays in an encrypted cache in your own Windows
  profile.
- **On-premises server accounts live in the Windows Credential Manager**, where you can see and
  remove them from the Control Panel without going through the application. The "Remember the
  password" box starts **unticked**: saving the password of a production administrator has to be a
  choice, not a default.

Read these before you act on a production system:

- **Stopping or restarting a production instance interrupts the service** — users disconnected,
  running operations aborted. Do it in a maintenance window.
- **Publishing an extension changes the target.** Try it on a test instance or a sandbox
  environment first, never straight in production.
- **On premises, the ForceSync mode uninstalls and republishes a version already present**, and
  applies schema changes even when they cause data loss. A second explicit confirmation is asked
  for.
- **Online, the Force Sync schema mode allows destructive schema changes**: the data of the tables
  that are modified or removed can be lost irreversibly. A second explicit confirmation is asked
  for.

---

## Usage data

DYNAMO can send **anonymous usage counts**, so that which commands are actually used, and on which
Business Central versions, can decide what gets improved. Names of servers, instances, tenants,
databases, accounts, companies and extensions never leave the machine, nor do paths or the text of
error messages.

It is switched off in *Settings > Privacy*, and takes effect immediately. What is waiting to be sent
sits in a plain-text file in your user profile that you can read with Notepad and delete at any
time.

The full notice is in **[PRIVACY.txt](PRIVACY.txt)**, and on that same page inside the program.

---

## License

Proprietary software, all rights reserved. The end user license agreement is in
**[LICENSE](LICENSE)** ([Italian version](LICENSE.it)). By installing or using the program you
accept its terms.

The application includes third-party components: their notices are in
**[THIRD-PARTY-NOTICES.txt](THIRD-PARTY-NOTICES.txt)** and are shown in the application under
*About > Third-party components*.

> Microsoft, Dynamics and Business Central are registered trademarks of Microsoft Corporation.
> DYNAMO is not affiliated with or sponsored by Microsoft.

---

## Reporting a problem

Open an [issue](../../issues). For anything that looks like a security problem, please read
[SECURITY.md](SECURITY.md) first.

When reporting, never paste server names, instance names, tenant identifiers, user names or
credentials: an issue is public. The version number, what you did and what happened are enough to
start.
