# TruthNotReality

Public file host for the TruthNotReality daily series, so Metricool can fetch files by URL.

## Where things go

- `songs/` — the Suno song for each video, `<work id>.mp3` (1-5 MB). The Grok bot puts it here and tells the Hill Command Center with `set_song`.
- `videos/` — only videos that are queued or just posted. Finished, posted videos get removed (see below).

## Size rules (GitHub asks repos to stay under ~1 GB; files over 100 MB are blocked)

- Keep each video under about 20 MB (1080x1920, H.264, ~2.5 Mbps). The platforms re-compress anyway.
- Once a video is confirmed posted on all four accounts, delete its video and song from the repo.
- Deleted files stay in Git history. Because of that, large files should not pile up here; the history is squashed periodically.
- GitHub Releases would keep big files out of the repo, but sessions that run the daily job can't create Releases, so they are not used yet.

## Daily job

Claude builds the video, commits it here, schedules it in Metricool, and after it posts removes the files and logs it in the Hill Command Center.
