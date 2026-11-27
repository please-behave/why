# Interface principles

[DEC-0026](../why/decisions/DEC-0026.yaml) applies these principles to Please Behave web surfaces, including the cockpit and the documentation site.

1. **Purpose.** State the question each view answers in the view's requirement. Show the information needed to answer it in the view.
2. **Exceptions.** Put exceptions ahead of healthy states. Give healthy states subdued visual treatment.
3. **Records and summaries.** Give each record one row in a table and present summaries as widgets. Keep cells that identify a record on one line.
4. **Density and targets.** Use compact spacing by default and increase spacing around controls for coarse pointers. Give every interactive target a width and height of at least 24 CSS pixels.
5. **Hierarchy.** Give each region one visually primary element. Put links on names and use muted text for secondary content and zero counts.
6. **Status.** Show each status with a distinct symbol, a visible text label and the corresponding color from the [visual identity](README.md#status-tokens).
7. **Previews.** Make all information and navigation available without hover, including when details appear in a preview. Keep a preview that contains links open while the pointer is over it or keyboard focus is inside it.
8. **Shared components.** Implement each recurring element as one shared component and use its styling consistently across views.
9. **Review.** Review each interface change on the component repository's review sheet before and after the change, and record both sets of measurements in the commit message body. For the cockpit, use the [cockpit preview review sheet tracked in issue 116](https://github.com/please-behave/cockpit/issues/116).
