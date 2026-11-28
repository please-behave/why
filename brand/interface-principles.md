# Interface principles

[DEC-0026](../why/decisions/DEC-0026.yaml) applies these principles to Please Behave web surfaces, including the cockpit and the documentation site.

1. **Purpose.** State the question each view answers in the view's requirement. Show the information needed to answer it in the view.
2. **Exceptions.** Put exceptions ahead of healthy states. Give healthy states subdued visual treatment.
3. **Records and summaries.** Give each record one row in a table and present summaries as widgets. Keep cells that identify a record on one line.
4. **Density and targets.** Use compact spacing by default and increase spacing around controls for coarse pointers. Give every interactive target a width and height of at least 24 CSS pixels.
5. **Hierarchy.** Give each region one visually primary element. Put links on names and use muted text for secondary content and zero counts. Use the [interface palette](palette.md) for text, links, focus and surfaces.
6. **Display forms.** Follow the [display forms](#display-forms).
7. **Previews.** Make all information and navigation available without hover, including when details appear in a preview. Keep a preview that contains links open while the pointer is over it or keyboard focus is inside it.
8. **Shared components.** Implement each recurring element as one shared component and use its styling consistently across views.
9. **Review.** Review each interface change on the component repository's review sheet before and after the change, and record both sets of measurements in the commit message body. For the cockpit, use the [cockpit preview review sheet tracked in issue 116](https://github.com/please-behave/cockpit/issues/116).

## Display forms

- **Outcomes.** Show each verdict, status or verification result as a distinct symbol and a visible text label, both in the corresponding [status color](palette.md#status-tokens). Leave both unframed.
- **Outcome wording.** Use exactly one label per outcome. Use `Pass`, `Warn`, `Fail`, `Error`, `Not run` and `No evidence` with the same wording and capitalization in every view, popup and count. Convert API outcome values to these labels before display.
- **Counts.** Show outcome counts as `<number> <outcome label>`, such as `1 Warn` or `3 Not run`. Use the same label for every count without inflecting it.
- **Row classifications.** Show a rule kind, blocking state or other row classification in a tinted rectangle with a small corner radius.
- **Object references.** Show references such as a Rule Set or a repository on the dashboard map as fully rounded capsules that link to the referenced object. In a table heading, make the object's name the heading link and omit the capsule.
- **Repository references.** Show `organization/repository` on one line, with the link to the repository on the `repository` part.
- **Popups.** Use a popup only to add information the view does not already show, such as the full value of truncated text or an explanation. Omit repeated visible text.
- **Times.** Show timestamps relative to now, for example `4 days ago`. Show the exact time in the viewer's local time zone in a popup that follows the popup rule, in accordance with [DEC-0027](../why/decisions/DEC-0027.yaml). Label the time when the system received a fact `Reported` in every view.
- **Versions.** Wherever a Rule Set or rule name appears, append its version, when available, in the form `Name · major.minor`. Use the middle dot as the separator and omit any version prefix. Display release versions exactly as reported, as free text.
- **Separators.** Use a middle dot only between two pieces of information in a row. Omit it after the last item.
