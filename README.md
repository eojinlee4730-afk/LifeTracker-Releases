# LifeTracker

LifeTracker is an Android app and a free local-only Web/PWA for recording workouts, food intake and bodyweight, and comparing daily records with your plans.

## Quick Summary

- Independently timed workout sessions, resistance sets, cardio and one shared rest countdown.
- Food intake, calories/macros and independent Workout/Diet Programs.
- Calendar, Records, exercise progress and daily summary images.
- Session-aware XLSX Programs, reusable presets, duplicate-safe actual History XLSX merge and full JSON backups.
- Local SQLite storage, configurable Today body/recovery metrics, English/Korean and Metric/Imperial display.

Each Today Food has an independent Edit action for its actual quantity and portion/g unit. Nutrition scales from that occurrence’s frozen reference. Cross-unit conversion requires an explicit serving weight. Reusable Food Library definitions and other historical occurrences remain separate. New Programs open from a minimal inactive root without activation or broad analytics work.

## Download

**Latest version: v1.0.15 (build 34)**

[**Open the latest release and download the APK**](https://github.com/eojinlee4730-afk/LifeTracker-Releases/releases/latest)

Current APK: [LifeTracker-v1.0.15-build34.apk](https://github.com/eojinlee4730-afk/LifeTracker-Releases/releases/download/v1.0.15/LifeTracker-v1.0.15-build34.apk)

Play Store bundle: [LifeTracker-v1.0.15-build34.aab](https://github.com/eojinlee4730-afk/LifeTracker-Releases/releases/download/v1.0.15/LifeTracker-v1.0.15-build34.aab)

### Install or update

1. Download the APK and open it on Android.
2. If prompted, allow installation from the browser or file manager you used.
3. Install over your existing LifeTracker version to update.

**Do not uninstall LifeTracker if you want to preserve its local data.** Data is stored on your device; uninstalling may remove it. Export a backup before making significant changes or moving devices.

## Web / PWA

[**Open LifeTracker Web**](https://eojinlee4730-afk.github.io/LifeTracker-Releases/app/) — installable in supported browsers, with offline tracking after the first successful online load. Hosting cost: **$0/month**.

Web records stay in browser-local IndexedDB. There is no account, automatic Android/Web sync or server backup. Transfer data manually with JSON backups in Menu → Data Management → Backup & Restore. Clearing site data or private browsing can remove records; export backups regularly. Browser rest alerts are less capable than Android native alarms and depend on browser permissions/background policies.

- Live English/Korean language changes now refresh navigation labels, screen-reader actions and screen content without resetting navigation; the selected language persists after its queued save completes.

## Features

### Workout Tracking and Timer

Record actual weights, reps, RPE and completed/skipped sets, add extra sets or exercises, and keep exercise notes. Muted, dark-surface vector boxed checks distinguish incomplete, partial and completed work without relying on color alone. Exercise and Workout status derive from participating children: all incomplete is gray, all complete is green, and mixed states are orange. Session indicators remain independent. Supported exercise tracking modes include resistance, bodyweight and cardio metrics. Completing an item before starting offers a confirmation that starts the workout and performs that exact action.

Start, pause, resume and finish the tracked workout for a date. Elapsed time uses timestamps and excludes pauses. Finish is prominent at both top and bottom. Numeric fields keep a stable input and local draft during focus changes; blur/Done/navigation commits are deduplicated. All-mode editing highlights and mirrors the current set and every set below it in the same exercise and field, including existing/completed values. The scope toolbar remains available across editable dates and direct field handoffs. Switching All back to 1 Set before commit cancels the pending lower-row changes. Set rows group Weight × Reps beside a separated RPE field. Finishing first saves the actual session, then offers to patch changed weight/reps and explicitly reusable Program notes into the exact originating occurrence. Actual exertion RPE, diary comments, extra exercises and session timing stay History-only; newer conflicting Program values are preserved. A confirmed **Reset Today's Workout** clears that day's actual workout state while retaining the planned workout, Diet and other dates.

New numeric selections include only the editable number, with units outside the selection. Actual memos remain user text. Reusable Program notes are labeled separately; new catalog instructions are not copied into new occurrence memos, and canceling a new Activity discards its unsaved draft.

### Optional Automatic Progressive Overload

Open the dedicated Progressive Overload control beside Program activation to configure this independently of active/inactive status. Enable this explicitly before activating a Workout Program, or change it later from Program details. The default uses the highest actual RPE among completed prescribed working sets: RPE ≤8 increases load, 8.5–9 holds, and high RPE, missed work or missing RPE hold. Advanced Settings provide thresholds, failure/high-RPE reductions, increments, available equipment steps, per-exercise overrides, minimum sets, prescribed-rep checks, aggregation and an optional increase cap. Defaults use a conservative editable 2.5 kg increment; equipment steps must be configured when needed.

Decisions apply to one exact next Daily/Weekly/N-week occurrence using Program, week, day, session and exercise identities. Duplicate exercises can use explicit chain keys. Finished actuals remain immutable. Each source has a durable decision; newer Program edits or edited/started future occurrences are preserved with a compact warning. Untouched future snapshots follow the revised prescription. Disabling stops future decisions without undoing prior changes. JSON backups preserve settings and decision provenance; XLSX retains the existing prescription exchange format.

Today Diet displays each date’s macro target directly beneath its actual intake. Stored date targets and explicit overrides take priority; unspecified goals may use the same date’s planned food snapshot. Unknown targets show a dash. Number/unit pairs stay together; calories display as whole kcal and macros use at most one decimal without changing stored precision.

### Today Body and Recovery Metrics

The settings icon beside the Today Tracking header chevron opens Today Tracking Fields. It is separate from expand/collapse and controls the order and visibility of 18 compact daily measurements: bodyweight, body fat, skeletal muscle/muscle mass, five circumferences, sleep duration/quality, resting heart rate, steps, water, energy, stress, soreness and hunger. Bodyweight remains enabled by default; other measurements are optional. Hiding a field preserves its records. Weight uses the existing table; other measurements use an additive daily table with canonical kg/cm/minutes/mL values and indexed date/metric access. Full JSON backups include all these measurements. Bodyweight History XLSX preserves canonical weight values; other optional health measurements currently use the full backup. Schema-v2 Workout History appends activity calculation metadata and still accepts schema-v1 files.

Linked Exercises explicitly connect adjacent occurrences within one session. A linked group moves as a block; checking a set first commits its active numeric draft and validates required actual RPE, then rotates immediately to the next member with remaining work and starts rest once. Keyboard Done retains its commit-only role; invalid RPE blocks linked completion. Today links stay local to that actual session. Program links materialize into future Today occurrences and can be roundtripped through optional LinkGroup/LinkPosition spreadsheet fields.

### Workout Programs

Create, edit, duplicate, archive, delete and select Workout Programs independently from Diet Programs. Daily, Weekly and N-week schedules support recurrence-specific editing and cycle alignment. Weekly lists Monday–Sunday; N-week schedules use configured weeks and end behavior. The latest activated Program is authoritative for untouched current/future planning, including dates previously opened for viewing. Already edited, started, imported or completed actual workouts retain their origin and contents. Workout and Diet activation remain independent. Program edits do not rewrite historical actual logs. Navigation retains the immediate parent when going Back.

### Diet Tracking

Track consumed amounts and actual calories, protein, carbohydrates and fat. Use foods from the library or manual entries; direct macro logging is also available at meal/day level. Planned and actual nutrition remain separate. Removing a planned food from Today affects that date rather than deleting it from its Program.

### Diet Programs

Plan meals and food portions with Daily, Weekly or N-week recurrence and optional nutrition targets. Each planned food occurrence can be enabled/disabled without losing its values, edited while disabled, re-enabled or permanently deleted separately. Disabled foods do not contribute to planned nutrition. Duplicate occurrences are independently controlled; prior consumed food logs remain intact.

Programs & Plans, Libraries and Data Management each have their own Menu destination. Program lists support persisted grip-handle ordering. Details include a tappable name with a pencil, explicit Active/Inactive control, start date, recurrence, end behavior and confirmed deletion. Week/day screens focus on their own content. A day can contain multiple planned sessions; actual sessions have independent start/pause/finish timing. Fresh installations have one Example Workout Program and one Example Diet Program. Shared numeric/text inputs use visible dark boxes and a restrained focus border; automatically derived outputs remain visually distinct. They reveal the focused field above the keyboard and measured scope toolbar while preserving raw active drafts.

### Exercise and Food Libraries

Browse/search built-in exercises and foods, manage custom entries and favorites, and use library entries in plans and actual logs. Custom Exercise has six draft-based multi-select metadata sheets and a nonnegative kcal/hour metadata field; existing aliases remain searchable without an alias-editing field. The rate does not replace the current completed-work/MET calorie engine. Custom creation and current-session replacement patch only the affected occurrence and preserve session/set identities, timers and unrelated edits. The Dumbbell Rear Delt Fly name is corrected while retaining its stable library identity; the genuine Shoulder Press remains separate. Stored identities keep separate occurrences distinct. Missing nutrition values remain distinguishable from recorded zero.

### Rest Timer

One global ON/OFF setting applies to all exercises, with independent saved durations per exercise. Eligible completed resistance sets can start the single active countdown; a later trigger replaces it. Turning the global switch OFF cancels the countdown rather than announcing completion. Android native scheduling supports background completion notification/vibration, subject to permissions, notification settings and device policies. The compact card has a timestamp-derived countdown, exercise name and thin progress bar. +30 extends, Skip cancels, and × only hides the countdown. Completion stays visible briefly; transitions respect reduced motion.

### Calories

Workout burn combines completed resistance work, recorded cardio and Other Activity once. Resistance uses a bounded completed-set work/time estimate and bodyweight/intensity inputs; idle session time alone contributes zero resistance calories. Other Activity accepts optional explicit kcal that overrides its estimate. Missing required inputs can leave estimates unavailable. Semantic readouts round kcal to whole numbers, macros/RPE/MET/speed to at most one decimal, and distance to two; stored values and active drafts retain their precision. Walking/running estimates use speed and grade within supported ACSM workload ranges; cycling uses speed bands unless MET is explicitly overridden. Inputs outside the supported speed/grade range show an unavailable estimate with an explanation. Activity duration uses separate minute/second inputs. Below memo, Calculation selects Auto (the last two explicitly edited distance/time/speed values determine the third) or Manual (all three remain independent). Current activities save that interpretation; completed/imported History retains its snapshots. Activity presets retain duration, motion values, calculation mode and explicitly authored memo/intensity settings when added to Today; viewing untouched prescribed values alone does not create recorded History. Calories use an explicit date weight or the latest applicable weight at/before the date, without inventing a weight record. These are estimates, not measured physiological expenditure.

### Calendar, Records and Exercise Progress

Calendar shows separate Workout and Diet states for each date. Optional achievement criteria have independent Workout and Diet ranges. Fresh settings use Orange 50–150% and Green 80–120%, while valid saved custom ranges and legacy thresholds retain their values. Both domains use red/orange/green/orange/red bands with validated lower and upper bounds. Planned Workout completion remains capped at 100%. Diet percentage uses the date's calorie target when available, with a macro-only fallback. The displayed percentage and color share the same classifier. Settings changes reclassify cached numeric facts immediately.

Actual Exercise Memos stay with their performed occurrence and session. History and Exercise Progress read that same saved memo, with separate entries for repeated same-day sessions. Finish captures the active text draft and waits for persistence. Actual Memos remain separate from reusable Program notes and roundtrip through History XLSX.

Records contains All Records, Daily Records, Exercise Progress and Adherence in that order. All Records keeps bodyweight, nutrition and workout charts together. A shared top filter selects 7, 30, 90 days or exact custom dates and follows navigation across Records pages. Statistics, charts, lists and Adherence use that period. Unavailable averages and ratios remain distinct from recorded zero. Child routes retain their Records parent on Back. Adherence uses localized labels and is no longer a Menu destination. Menu lists Presets before Data Management.

Activating a Diet Program updates today's targets and replaceable planned Foods while preserving consumed occurrence identities, actual nutrition and frozen reference snapshots. Today, Calendar, Records and Adherence read the same dated target. Past and imported historical snapshots retain their targets. Opening, expanding or focusing an unchanged dated plan creates no actual workout, food, bodyweight or health record. Meaningful edits/start/check actions create actual data lazily. Cached aggregates and bounded selected-range queries support Records and Exercise Progress; charts load locally and respect reduced motion.

### Daily Summary

Preview daily Workout/Diet summaries, save generated PNGs to a system-selected folder, or share them with another app. Summaries use actual recorded work/intake while retaining planned comparisons. LifeTracker does not browse or read your photo library and does not request broad photo/media access.

Screen and image share the same recorded-data projection. Session active time is counted once, with applicable completed activity duration when no session clock exists. Preview and capture measure full intrinsic content independently of their scaled display bounds. A separate noninteractive surface captures the complete Summary beyond the phone viewport at 1080px width. PNG dimensions are checked before saving. Images above the 16 MP allocation limit show a localized message directing you to export an individual Session; content is never silently cropped or made unreadably small.

### Import / Export and Templates

Menu → Data Management separates Program Import / Export, Templates, actual History files and Backup & Restore. Programs & Plans also links to that shared area and has bottom Save Template / Import Data buttons. Templates opens a two-choice modal in place; both entry points use the same generator. Import shortcuts use the guarded Program preview, separate from History. Workout File and Diet File have parallel Import File / Save Template actions, and each expandable Program row exports only when requested. Program detail has the same export action at the bottom. Start Date and the prominent Recurrence heading share a compact wrapping metadata group. Supported exercise/food/activity deletes and planned-content edits update immediately while persistence stays serialized; failures reconcile without raw database text.

New schema-v4 Workout/Diet workbooks use English or Korean visible headers, dropdowns, instructions and example labels based on app language; hidden stable keys keep either language importable in either UI. Typed numeric fields, one-weekday-per-row rules, recurrence requirements and library identities are validated before saving. Every EXAMPLE row is excluded; two-row sample blocks demonstrate separate foods/sets and a sample-only workbook creates no Program. Both templates include strict AI/human one-item-per-row instructions. Obvious combined names or prose require correction and are never automatically split. Workbook planning metadata preserves rich prescriptions and nutrition snapshots; it contains no actual session history. Legacy canonical Workout/Diet sheets remain supported. Exported Program files and templates use the same generator. The workbook engine loads only when needed and uses its polyfill-free build to preserve React Native's Promise implementation and scheduler. Instructions use ordinary cells and RowNote rather than native Excel comments. Imported comment/VML annotations are ignored without changing cell values, validation rules or example-row markers. Exact and uniquely normalized catalog names/aliases resolve automatically. Similar/ambiguous names require explicit mapping; repeated values share a selection. Diet mapping can search the Food Library or explicitly create a reviewed Food without restarting. Unknown names never create Library entries automatically. Custom catalog names are allowed through mapping, while structural enums retain strict dropdowns. Shared Workout/Diet presets remain available.

Started/performed workout occurrences keep their materialized exercise, set and session snapshots when the active Program is edited or switched, including on today's date. Untouched future occurrences can follow updated plans. Workout/Diet Programs remain independent.

Data Management exports/imports actual Workout, Diet and Bodyweight History separately or in one versioned XLSX workbook. Imports validate before writing, merge without deleting records, skip identical identities and preserve conflicting existing records. Duplicate checks use the canonical record after SQLite applies its existing session/completion defaults. Older import metadata is repaired only for the verified default-session discrepancy while all other stored fields match; History values are preserved. Normalized child sheets preserve multiple same-day sessions and historical food snapshots; canonical units remain metric. Full JSON backup/restore remains the safest complete restoration format.

### Units, Appearance and Language

Choose Metric or Imperial display without rewriting canonical measurements. Imperial weight/distance displays use consistent decimal formatting. English and Korean have complete dictionary coverage; chart titles, filters, legends/tooltips, library filters and meal labels use the selected language at render time; sparse additional locales use consistent English UI fallback with locale-aware dates/numbers. A system-language preference is available. **Dark appearance is the supported theme in this build.**

### Dialogs and Action Feedback

Confirmation dialogs share LifeTracker's dark surface, readable typography and equal-height actions, with Cancel before the primary/destructive choice. Program activation shows immediate localized progress, blocks duplicate submissions and refreshes active/inactive state after its atomic database transaction. Import, export, template generation, restore and editor saves show consistent busy feedback; critical committing dialogs cannot be dismissed with Back.

### Data, Offline Storage and Android Integration

Core tracking works locally/offline using SQLite on Android and SQLite/WASM stored in IndexedDB on Web. Versioned migrations preserve records; analytics caches are disposable and rebuilt as needed. JSON backup/restore and file sharing support local data management. Android integration includes native rest alarms/notifications, generated PNG file saving and file sharing. This distribution repository contains documentation and signed release artifacts, not the private application source.

## Version Information

- Current Version: **v1.0.15**
- Android Build: **34**
- Package: `com.lee2300.LifeTracker`

## Known Limitations

Android and browser records remain separate without cloud sync. History XLSX is a conservative actual-record merge, not a replacement for full JSON backup/restore. Large imports use resumable transaction chunks; conflicting existing rows are retained. Native notifications/vibration depend on Android permissions/settings. Release automation validates builds and signatures, but does not establish physical-device touch, layout, vibration or installed-data-retention behavior.
