Architecture and core principles are defined in `docs`. At the start, run `tree docs`. Use the filenames to identify and read the documents relevant to the task before proceeding.

Behaviour lives in 'features/**/*.feature'. Those files are the source of truth and belong to the user. Do not tree or read them up front: 'tree features' only when checking a new scenario against existing ones, implementing a ticket, or reviewing. Never create, edit or delete a scenario to make a test pass. 

Document only surprises: the delta between what you already know and what this project does. Document names must say what the document is for without opening it - 'how-to-run-tests.md', never 'notes-3.md'.

Folder 'records' is an archive of old records, transcripts and ideas - never tree, search, edit or use it unless the user explicitly asks.
