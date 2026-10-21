# LifeTracker

LifeTracker is an Android app and a free local-only Web/PWA for recording workouts, food intake and bodyweight, and comparing daily records with your plans.

## Quick Summary

- Independently timed workout sessions, resistance sets, cardio and one shared rest countdown.
- Food intake, calories/macros and independent Workout/Diet Programs.
- Calendar, History, exercise progress and daily summary images.
- Session-aware XLSX Programs, reusable presets, duplicate-safe actual History XLSX merge and full JSON backups.
- Local SQLite storage, English/Korean and Metric/Imperial display.

## Download

**Latest version: v1.0.5 (build 24)**

[**Open the latest release and download the APK**](https://github.com/eojinlee4730-afk/LifeTracker-Releases/releases/latest)

Current APK: [LifeTracker-v1.0.5-build24.apk](https://github.com/eojinlee4730-afk/LifeTracker-Releases/releases/download/v1.0.5/LifeTracker-v1.0.5-build24.apk)

Play Store bundle: [LifeTracker-v1.0.5-build24.aab](https://github.com/eojinlee4730-afk/LifeTracker-Releases/releases/download/v1.0.5/LifeTracker-v1.0.5-build24.aab)

### Install or update

1. Download the APK and open it on Android.
2. If prompted, allow installation from the browser or file manager you used.
3. Install over your existing LifeTracker version to update.

**Do not uninstall LifeTracker if you want to preserve its local data.** Data is stored on your device; uninstalling may remove it. Export a backup before making significant changes or moving devices.

## Web / PWA

[**Open LifeTracker Web**](https://eojinlee4730-afk.github.io/LifeTracker-Releases/app/) — installable in supported browsers, with offline tracking after the first successful online load. Hosting cost: **$0/month**.

Web records stay in browser-local IndexedDB. There is no account, automatic Android/Web sync or server backup. Transfer data manually with JSON backups in Menu → Data Tools. Clearing site data or private browsing can remove records; export backups regularly. Browser rest alerts are less capable than Android native alarms and depend on browser permissions/background policies.

## Features

### Workout Tracking and Timer

Record actual weights, reps, RPE and completed/skipped sets, add extra sets or exercises, and keep exercise notes. Supported exercise tracking modes include resistance, bodyweight and cardio metrics. Completing an item before starting offers a confirmation that starts the workout and performs that exact action.

Start, pause, resume and finish the tracked workout for a date. Elapsed time uses timestamps and excludes pauses. Finish is prominent at both top and bottom. A confirmed **Reset Today's Workout** clears that day's actual workout state while retaining the planned workout, Diet and other dates.

### Workout Programs

Create, edit, duplicate, archive, delete and select Workout Programs independently from Diet Programs. Daily, Weekly and N-week schedules support recurrence-specific editing and cycle alignment. Weekly lists Monday–Sunday; N-week schedules use configured weeks and end behavior. Program edits do not rewrite historical actual logs. Navigation retains the immediate parent when going Back.

### Diet Tracking

Track consumed amounts and actual calories, protein, carbohydrates and fat. Use foods from the library or manual entries; direct macro logging is also available at meal/day level. Planned and actual nutrition remain separate. Removing a planned food from Today affects that date rather than deleting it from its Program.

### Diet Programs

Plan meals and food portions with Daily, Weekly or N-week recurrence and optional nutrition targets. Each planned food occurrence can be enabled/disabled without losing its values, edited while disabled, re-enabled or permanently deleted separately. Disabled foods do not contribute to planned nutrition. Duplicate occurrences are independently controlled; prior consumed food logs remain intact.

Programs, Libraries and Data Tools each have their own Menu destination. Program lists support persisted grip-handle ordering. Details include a tappable name, explicit Active/Inactive control, start date, recurrence, end behavior and confirmed deletion. Week/day screens focus on their own content. A day can contain multiple planned sessions; actual sessions have independent start/pause/finish timing. Fresh installations have one Example Workout Program and one Example Diet Program. Shared numeric/text inputs reveal the focused field above the keyboard.

### Exercise and Food Libraries

Browse/search built-in exercises and foods, manage custom entries and favorites, and use library entries in plans and actual logs. Stored identities keep separate occurrences distinct. Missing nutrition values remain distinguishable from recorded zero.

### Rest Timer

One global ON/OFF setting applies to all exercises, with independent saved durations per exercise. Eligible completed resistance sets can start the single active countdown; a later trigger replaces it. Turning the global switch OFF cancels the countdown rather than announcing completion. Android native scheduling supports background completion notification/vibration, subject to permissions, notification settings and device policies.

### Calories

Workout burn combines completed resistance work, recorded cardio and Other Activity once. Resistance uses a bounded completed-set work/time estimate and bodyweight/intensity inputs; idle session time alone contributes zero resistance calories. Other Activity accepts optional explicit kcal that overrides its estimate. Missing required inputs can leave estimates unavailable. These are estimates, not measured physiological expenditure.

### Calendar, History and Exercise Progress

Calendar shows separate Workout and Diet states for each date. Optional goal completion uses stored planned-food totals and scheduled work, configurable low/high Diet bounds (default 50 / 90 / 110 / 150%) and a separate Workout Green boundary. Choose percentages or status colors. Review dated records and bodyweight. History and Summary use cached aggregates and selected date ranges; charts load locally and respect reduced motion. Exercise Progress provides identity-specific charts and bounded session details for actual work. Diet adherence and nutrition/bodyweight trends help compare records with plans.

### Daily Summary

Preview daily Workout/Diet summaries, save generated PNGs to a system-selected folder, or share them with another app. Summaries use actual recorded work/intake while retaining planned comparisons. LifeTracker does not browse or read your photo library and does not request broad photo/media access.

### Import / Export and Templates

Import/export Workout and Diet XLSX files with Daily/Weekly/N-week layouts. Workout files retain the original five columns and add optional Session, SessionName, ExerciseKey, Notes and RPE fields; old files import into Session 1. Diet files preserve optional Enabled state; older files without it default foods to enabled. Workout import offers file checking, exercise mapping and guarded undo. Save blank templates, exercise-name lists and reusable Workout/Diet presets.

Data Tools exports/imports actual Workout, Diet and Bodyweight History separately or in one versioned XLSX workbook. Imports validate before writing, merge without deleting records, skip identical identities and preserve conflicting existing records. Normalized child sheets preserve multiple same-day sessions and historical food snapshots; canonical units remain metric. Full JSON backup/restore remains the safest complete restoration format.

### Units, Appearance and Language

Choose Metric or Imperial display without rewriting canonical measurements. Imperial weight/distance displays use consistent decimal formatting. English and Korean have complete dictionary coverage; sparse additional locales use consistent English UI fallback with locale-aware dates/numbers. A system-language preference is available. **Dark appearance is the supported theme in this build.**

### Data, Offline Storage and Android Integration

Core tracking works locally/offline using SQLite on Android and SQLite/WASM stored in IndexedDB on Web. Versioned migrations preserve records; analytics caches are disposable and rebuilt as needed. JSON backup/restore and file sharing support local data management. Android integration includes native rest alarms/notifications, generated PNG file saving and file sharing. This distribution repository contains documentation and signed release artifacts, not the private application source.

## Version Information

- Current Version: **v1.0.5**
- Android Build: **24**
- Package: `com.lee2300.LifeTracker`

## Known Limitations

Android and browser records remain separate without cloud sync. History XLSX is a conservative actual-record merge, not a replacement for full JSON backup/restore. Large imports use resumable transaction chunks; conflicting existing rows are retained. Native notifications/vibration depend on Android permissions/settings. Release automation validates builds and signatures, but does not establish physical-device touch, layout, vibration or installed-data-retention behavior.
