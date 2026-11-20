# Cloud / mobile bootstrap - read this first

This repository is only a launcher. Joe's real working folder is **`Claude engine`** in his
OneDrive (The Letting Experts, Microsoft 365). Everything - the operating manual, skills,
diary, scripts and documents - lives there, not in this repo. Do not copy business files or
client data into this repository.

## Step 1 - load the real manual (every session, before anything else)
Using the Microsoft 365 connector (`read_resource`), read:

`file:///b!70Ms8u1ZvEa-lnPFmOekD7BraEEAGp9Br7VQBYeVyFnUPvwy3z-yQrDtJlPCFJHx/Claude engine/CLAUDE.md`

Follow it exactly as if this session had been opened on that folder on Joe's desktop. That
manual is the source of truth and wins over this file wherever they differ, except for the
cloud differences listed below.

## How the manual's paths map to OneDrive
- Drive (Joe's whole OneDrive): `b!70Ms8u1ZvEa-lnPFmOekD7BraEEAGp9Br7VQBYeVyFnUPvwy3z-yQrDtJlPCFJHx`
- A path in the manual such as `Skills/morning-brief.md` or `Engine/diary.md` means
  `file:///<drive>/Claude engine/Skills/morning-brief.md`, and so on.
- The rest of Joe's OneDrive is reachable the same way from the drive root
  (`file:///<drive>/` lists it). Use `sharepoint_search` / `sharepoint_folder_search` to find
  things by name or content.
- Desktop paths like `C:/Users/joeyp/OneDrive - The Experts.../Claude engine/...` are the same
  files: drop everything up to and including `Claude engine/` and use the mapping above.

## Reading and writing files in the cloud
- Read: `read_resource` with the `file:///` URI. Large files have pages - read narrowly
  (token diet), e.g. only the last page of `Engine/diary.md`.
- Edit an existing file (e.g. append to the diary): read it, then write the full new content
  back with `sharepoint_update_file` (driveId + item id). OneDrive keeps version history.
- New file: `sharepoint_upload_file`. Move (never delete): `sharepoint_move_item` into
  `To sort`. Rename: `sharepoint_rename_item` - show Joe first, as the manual says.
- To run one of the Node scripts in `Engine/`, download its text with `read_resource`, save
  it to the scratchpad, adjust the Windows paths, and run it with `node` here. Put the outputs
  back in OneDrive with the upload tools. Never leave client data in this repository.

## Cloud differences from the desktop (say so to Joe when they matter)
- **Not available here:** Claude in Chrome (so TLE OS cannot be reached), PowerShell scripts
  (`*.ps1`), the C# photo tools, anything on Joe's PC itself. For those, Joe uses the desktop.
- **Scheduled tasks** on the desktop do not run from here; cloud scheduled tasks can be set
  up separately if Joe asks.
- Connectors available in the cloud: Microsoft 365 (OneDrive, Outlook, Teams, calendar),
  Gmail, Google Calendar, Google Drive, Canva.
