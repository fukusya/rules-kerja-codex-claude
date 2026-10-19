# Cara Pasang Rules Ini ke Project Kamu

4 file yang udah disiapin:

| File | Ditaruh di | Fungsi |
|---|---|---|
| [`global/CLAUDE.md`](global/CLAUDE.md) | `~/.claude/CLAUDE.md` + `~/.codex/AGENTS.md` (folder home, 1x aja per komputer, berlaku ke SEMUA project) | Identitas kamu + gaya komunikasi + aturan lintas-project |
| [`project-template/AGENTS.md`](project-template/AGENTS.md) | `AGENTS.md` di folder utama tiap project (OKR, ATS, Siklus Kulit, Time Management, WhatsApp extension) | Alur kerja Claude↔Codex, permission, definition of done — diisi manual per-project |
| [`project-template/settings.example.json`](project-template/settings.example.json) | `.claude/settings.json` di tiap project | Yang beneran MAKSA (git push wajib nanya, dll) — bukan cuma tertulis |
| [`project-template/HANDOFF_CONTEXT.md`](project-template/HANDOFF_CONTEXT.md) | `HANDOFF_CONTEXT.md` di folder utama tiap project | Ringkasan status terkini — ini yang dibaca sesi chat BARU, bukan transkrip lengkap. Dirujuk dari AGENTS.md, wajib diupdate sebelum sesi ditutup. |

## Soal transkrip lama (chat baru bakal "lupa" konteks?)

Transkrip yang udah kamu simpen ([lihat daftar di bawah](#transkrip-per-project)) **ga perlu dipaste ulang ke chat baru** — kepanjangan, malah boros token kayak insiden 88k-token kemarin. Caranya:

1. Isi `HANDOFF_CONTEXT.md` tiap project dengan ringkasan singkat: lagi ngerjain apa, keputusan yang udah final, dependency yang udah/belum divalidasi.
2. Tiap sesi baru WAJIB baca `HANDOFF_CONTEXT.md` dulu (udah diatur di `AGENTS.md` langkah 0).
3. Transkrip lengkap cuma dibuka kalau beneran butuh tau alasan detail di balik keputusan lama — dirujuk lewat link di `HANDOFF_CONTEXT.md`, bukan dibaca utuh tiap sesi.

### Transkrip per-project

| Project | Repo | Transkrip Claude | Transkrip Codex |
|---|---|---|---|
| OKR | [transkrip-okr-dari-claude-codex](https://github.com/fukusya/transkrip-okr-dari-claude-codex) | [Claude](https://github.com/fukusya/transkrip-okr-dari-claude-codex/blob/master/TRANSKRIP-OKR-CLAUDE.md) | [Codex](https://github.com/fukusya/transkrip-okr-dari-claude-codex/blob/master/TRANSKRIP-OKR-CODEX.md) |
| ATS | [transkrip-candidate-tracker-to-ats](https://github.com/fukusya/transkrip-candidate-tracker-to-ats-dari-claude-codex) | [Claude](https://github.com/fukusya/transkrip-candidate-tracker-to-ats-dari-claude-codex/blob/master/claude/TRANSKRIP%20CLAUDE%20ATS) | [Codex](https://github.com/fukusya/transkrip-candidate-tracker-to-ats-dari-claude-codex/blob/master/codex/TRANSKRIP%20CODEX%20ATS) |
| Siklus Kulit | [siklus-kulit-app](https://github.com/fukusya/siklus-kulit-app) | [Claude](https://github.com/fukusya/siklus-kulit-app/blob/chat-transcript/Transkip%20Claude%20Siklus%20Kulit.md) | [Codex](https://github.com/fukusya/siklus-kulit-app/blob/codex/conversation-transcript/Transkip%20Codex%20Siklus%20Kulit.md) |
| Time Management | [time-management](https://github.com/fukusya/time-management) | [Claude](https://github.com/fukusya/time-management/blob/main/Transkrip%20Claude%20Time%20Management.md) | [Codex](https://github.com/fukusya/time-management/blob/main/Transkrip%20Codex%20Time%20Management.md) |
| WhatsApp | [recruitment-chat-assistant](https://github.com/fukusya/recruitment-chat-assistant) | [Claude](https://github.com/fukusya/recruitment-chat-assistant/blob/main/docs/conversations/Transkrip%20Claude%20WA%20extensions.md) | [Codex](https://github.com/fukusya/recruitment-chat-assistant/blob/main/docs/conversations/Transkrip%20Codex%20WA%20extensions.md) |

## Langkah Pasang (1x setup)

### 1. Pasang yang global (sekali aja, berlaku semua project)

```bash
mkdir -p ~/.claude
cp global/CLAUDE.md ~/.claude/CLAUDE.md
mkdir -p ~/.codex
cp global/CLAUDE.md ~/.codex/AGENTS.md
```

> Pindah/ganti komputer? Ulangi langkah 1 ini aja — file per-project udah ikut ke-clone bareng repo project-nya.

### 2. Pasang ke tiap project (ulangi buat OKR, ATS, Siklus Kulit, Time Management, WhatsApp extension)

```bash
cp project-template/AGENTS.md /path/ke/project/AGENTS.md
cp project-template/HANDOFF_CONTEXT.md /path/ke/project/HANDOFF_CONTEXT.md
mkdir -p /path/ke/project/.claude
cp project-template/settings.example.json /path/ke/project/.claude/settings.json
echo "@AGENTS.md" > /path/ke/project/CLAUDE.md
```

Terus **buka `AGENTS.md` dan `HANDOFF_CONTEXT.md` di project itu, isi bagian `[ISI DI SINI]`** — stack, command, struktur folder, batasan spesifik project itu. Kalau project udah punya `CLAUDE.md` isinya banyak, jangan langsung timpa — gabungin dulu bagian yang masih relevan ke `AGENTS.md`, baru `CLAUDE.md`-nya diringkas jadi cuma `@AGENTS.md`.

## Kalau nanti ada koreksi baru

- Kalau kesalahannya **spesifik 1 project** → tambahin ke bagian "Zona yang Pernah Bermasalah" di `AGENTS.md` project itu.
- Kalau kesalahannya **bisa kejadian di project manapun** (soal gaya komunikasi, cara kerja Claude↔Codex, dll) → tambahin ke `global/CLAUDE.md` di repo ini, commit, push, terus copy ulang ke `~/.claude/CLAUDE.md` dan `~/.codex/AGENTS.md`.
