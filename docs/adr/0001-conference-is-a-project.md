# A Conference is a Trilium Project, not a new note type

A Conference is stored in Trilium as a Project (`#type=project`, Project template, `~area` to a Conferenze hub), in one note holding its Agenda, Takeaways and Recap, rather than as a new `#type=conference` with its own template. A Conference has a start, an end and a status, which is what a Project already models, and reusing it leaves the Trilium schema untouched and shows Conferences in the Projects table for free.

## Considered Options

- **New `#type=conference` with a dedicated template**: more precise, but changes the system schema described in "Convenzioni per Claude" for one use case.
- **One note per Session**: a program runs to 50-100 Sessions, most never watched; only the Agenda lives in the note, and a Session becomes its own permanent note only when it earns a life beyond the Conference.
- **A note under Aree/Viaggi**: TREK and Viaggi are for leisure trips; a Conference's travel is improvised around the event and stays out of scope.
